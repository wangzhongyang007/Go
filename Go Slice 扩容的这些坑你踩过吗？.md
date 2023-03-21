## 前言

之前对Go语言for循环做了一次踩坑经验分享[《Go for range 一不小心就掉坑里了》](https://mp.weixin.qq.com/s?__biz=MzIyNjM0MzQyNg==&mid=2247486979&idx=1&sn=b6900099b78b0b638241df62d1f1bec7&chksm=e870a16edf072878538c153f2a08e5194d152d6a4733e0affbd9a5844b08eba0cfe2eedb0b66&token=1569670706&lang=zh_CN#rd)，大家直呼有用。

今天对切片Slice的append操作也做一次踩坑经验分享，希望对朋友们有所帮助，有用请三连支持。

## 知识重温

**切片底层结构定义**：包含`指向底层数组的指针`、`长度`和`容量`

```
type slice struct {
  array unsafe.Pointer
  len   int
  cap   int
}
```

**append操作**：可以是1个、多个、甚至整个切片（记得后面加...）；添加元素时当容量不足，则会自动触发切片扩容机制，产生切片副本，同时指向底层数组的指针发生变化

```
var nums []int
nums = append(nums, 1)
nums = append(nums, 2, 3, 4)
nums2 := []int{5, 6, 7}
nums = append(nums, nums2...)
fmt.Println(nums) //[1 2 3 4 5 6 7]
```

## 案例1：传值+未扩容

先来看看下面会输出什么结果？

```
func main() {
  s1 := make([]int, 0, 5)
  fmt.Println("s1切片: ", s1)
  appendFunc(s1)
  fmt.Println("s1切片: ", s1)
  fmt.Println("s1切片表达式: ", s1[:5])
}

func appendFunc(s2 []int) {
  s2 = append(s2, 1, 2, 3)
  fmt.Println("s2切片: ", s2)
}
```

输出结果：

```
s1切片:  []
s2切片:  [1 2 3]
s1切片:  []
s1切片表达式:  [1 2 3 0 0]
```

看到这个结果，大家就会有疑问了，**明明切片是引用类型，为什么s2 append了新元素后，s2是有值了但s1却还是空的，并且对s1用切片表达式却能获取到值呢？**

原因分析前，我们先来看看s1和s2到底是不是同一个切片，打印地址验证下

```
func main() {
  s1 := make([]int, 0, 5)
  fmt.Printf("s1切片地址: %p\n", s1)
  appendFunc(s1)
  //...
}

func appendFunc(s2 []int) {
  s2 = append(s2, 1, 2, 3)
  fmt.Printf("s2切片地址: %p\n", s2)
  //...
}

输出结果：
s1切片地址: 0xc000018150
s2切片地址: 0xc000018150
```

看到这就得**傻眼了，两个切片的地址都是同一个，s2修改后s1也应该同步修改，应该都有值啊**

我们还得继续再深究一下，`fmt包%p`打印的这个地址，到底是谁的地址

```
//fmt/print.go
func (p *pp) fmtPointer(value reflect.Value, verb rune) {
  var u uintptr
  switch value.Kind() {
  case reflect.Chan, reflect.Func, reflect.Map, reflect.Ptr, reflect.Slice, reflect.UnsafePointer:
    u = value.Pointer()
  default:
    p.badVerb(verb)
    return
  }
  //...
}

//reflect/value.go
func (v Value) Pointer() uintptr {
  k := v.kind()
  switch k {
  //...
  
  case Slice:
    return (*SliceHeader)(v.ptr).Data
  }
  panic(&ValueError{"reflect.Value.Pointer", v.kind()})
}
```

通过分析fmt包的源码，不难发现，**打印的地址，其实是切片里指向底层数组的指针存储的地址，并不是两个切片本身的地址**。同时也说明这两切片是指向同一个底层数组。

**原因正式分析**：

1.  **传值操作**，s1和s2是两个不同的切片变量，但是指向底层数组的指针是同一个；
1.  **长度和容量的变化**：s1 Len=0和Cap=5，后来未发生过变化；s2一开始被赋值时 Len=0和Cap=5，在append操作后，Len=3和Cap=5，同时底层数组值从`[0,0,0,0,0]`被修改成了`[1,2,3,0,0]`;
1.  **输出结果**，s1由于Len=0所以输出空[]，而s1用切片表达式，是基于底层数组`[1,2,3,0,0]`进行切片，所以输出结果为`[1,2,3,0,0]`；

## 案例2：传值+扩容

将案例1，append的元素个数超过切片容量，触发自动扩容，输出的结果又会是怎样的呢？

```
func main() {
  s1 := make([]int, 0, 5)
  fmt.Println("s1切片: ", s1)
  appendFunc(s1)
  fmt.Println("s1切片: ", s1)
  fmt.Println("s1切片表达式: ", s1[:5])
}

func appendFunc(s2 []int) {
  s2 = append(s2, 1, 2, 3, 4, 5, 6)
  fmt.Println("s2切片: ", s2)
}
```

输出结果：

```
s1切片:  []
s2切片:  [1 2 3 4 5 6]
s1切片:  []
s1切片表达式:  [0 0 0 0 0]
```

**原因分析**：

1.  **发生扩容后**，s2指向的底层数组会产生副本，导致s1和s2不再指向同一个底层数组；
1.  **长度和容量的变化**：s2 append后Len=6、Cap=10和底层数组值为`[1,2,3,4,5,6,0,0,0,0]`；s2的操作完全不影响s1的数据，s1仍然是Len=0、Cap=5和底层数组值为`[0,0,0,0,0]`；
1.  **输出结果**，s2由于Len=6所以输出`[1,2,3,4,5,6]`，s1由于Len=0所以输出空[]，而s1用切片表达式，是基于底层数组`[0,0,0,0,0]`进行切片，所以输出结果为`[0,0,0,0,0]`；

## 案例3：传址+不关心扩容

上面两个传值操作的例子，不管扩容与否，都不会影响原切片s1的长度和容量。如果我们**期望修改s2的同时也修改原切片s1，则需要用到切片指针，基于地址传递进行操作**。

```
func main() {
  s1 := make([]int, 0, 5)
  fmt.Println("s1切片: ", s1)
  fmt.Printf("s1切片地址: %p len:%d cap:%d\n", &s1, len(s1), cap(s1))
  appendFunc(&s1)
  fmt.Println("s1切片: ", s1)
  fmt.Println("s1切片表达式: ", s1[:5])
}

func appendFunc(s2 *[]int) {
  fmt.Printf("s2切片地址: %p len:%d cap:%d\n", s2, len(*s2), cap(*s2))
  //*s2 = append(*s2, 1, 2, 3)
  *s2 = append(*s2, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10)
  fmt.Printf("append后s2切片地址: %p len:%d cap:%d\n", s2, len(*s2), cap(*s2))
  fmt.Println("s2切片: ", *s2)
}
```

输出结果：

```
s1切片:  []
s1切片地址: 0xc00000c030 len:0 cap:5
s2切片地址: 0xc00000c030 len:0 cap:5
append后s2切片地址: 0xc00000c030 len:10 cap:10
s2切片:  [1 2 3 4 5 6 7 8 9 10]
s1切片:  [1 2 3 4 5 6 7 8 9 10]
s1切片表达式:  [1 2 3 4 5]
```

万变不离其宗，**传址操作，始终操作的是同一个切片变量**，append操作后，长度和容量都会同时发生变化，以及如果触发扩容，那么指向底层数组的指针，也都会同时发生变化。

## 总结

**切片传值操作**，append未触发扩容，会同时修改底层数组的值，但不会影响原切片的长度和容量；当触发扩容，那么会产生副本，后面的修改则会和原底层数组剥离开，互不影响。

如果期望在修改切片后，对原切片也发生修改，则可以使用**传址操作**，始终基于同一个切片变量进行操作。

## 联系我

我的微信：wangzhongyang1993

视频号：王中阳Go

公众号：程序员升职加薪之旅

欢迎关注 ❤️
