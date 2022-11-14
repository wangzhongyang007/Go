# Go
《Go语言学习路线图》在各大技术社区平台已被累积收藏超过1万次。让你少踩坑，高效学，Let's Go!

# 前言

为了方便大家能够按顺序系统的进行学习，我把之前整理的[Go语言学习专栏](https://juejin.cn/column/7064777730532835336)文章进行了梳理。

方便大家更系统的学习Go语言，**欢迎大家在评论区推荐、自荐优秀的Go文章**。

让我们手牵着手，一起走，少走弯路，又快又好的成为**Gopher**，Let's Go。

**建议大家先收藏，结合自己的情况合理安排学习计划，坚持学习打卡，可以在评论区留言。**

# 概览

首先分享了我的**学习经验**：讲一讲Go语言为什么值得学习？以及我是如何高效学习Go语言的。

然后就是刻意练习了，需要大家和我一样，坚持每天手撸代码，多敲多想：

通过对**Go基础篇**的学习，可以从Go小白升级成为能用Go撸代码的gopher。

通过对**Go进阶篇**的学习，可以从Go初级程序员升级为Go中级工程师。

通过**Go PHP JAVA类比篇**的学习，可以更好的理解Go的优势，更好的理解Go的设计思想。

**框架篇** 不仅对比了目前主流的Go框架，还重点讲解了GoFrame框架相关的知识点。

**GoFrame**是类似PHP-Laravel, Java-SpringBoot的Go企业级开发框架，非常值得大家学习。

最后，会通过几篇**应用实践**的文章收尾，带大家体验一下用Go开发企业项目的快乐。

> 说明：下面的文章没有标注作者信息的是我的文章；标明作者的都是优秀创作者投稿，经过筛选的优质文章。

# Go签约文章

很荣幸被掘金签约，近期我将持续更新Go进阶实战文章，欢迎关注：[# 签约专栏：Go语言进阶实战](https://juejin.cn/column/7140137480749547528)


# 为什么学Go?

[# Go语言为什么值得学习？](https://juejin.cn/post/7064778754979004447)

[# Go 在云原生时代的优势](https://juejin.cn/post/7110226868418117639)
作者：[# 宇宙之一粟](https://juejin.cn/user/3526889034751639)

# 学习经验分享

[# 回顾一下我的Go学习之旅 | Go 主题月](https://juejin.cn/post/6949109361331568670)

[# [译]如何真正学习Go 语言](https://juejin.cn/post/7061777327641853960)
作者：[# 宇宙之一粟](https://juejin.cn/user/3526889034751639)

[# 写Go最近踩的坑 | 日志、内聚和复用、gjson、调整心态](https://juejin.cn/post/7103887534299545613)

# 基础篇

## 数据类型

[#【Go基础】编译、变量、常量、基本数据类型、字符串](https://juejin.cn/post/6942795881049489438/)

[# Go const和iota 使用实战](https://juejin.cn/post/7068456474133364743/)

[# Go基础数据类型使用实战：int float bool](https://juejin.cn/post/7068457967133130782)

## 切片

[# Go slice切片详解和实战](https://juejin.cn/post/7071960543283642404)

[# Go slice切片详解和实战(2) make append copy](https://juejin.cn/post/7068573594879524894)

[# 深入理解 slice 非常硬核！](https://juejin.cn/post/7122495050067476510)
作者：[# 二牛QAQ](https://juejin.cn/user/2344623087289965)

## 数组

[# Go 数组详解和实战](https://juejin.cn/post/7072165701036802055)

[# Go map详解和实战](https://juejin.cn/post/7072905649708859429)

## rune

[# Go rune详解和实战](https://juejin.cn/post/7068726981159829541)

## 指针

[# Go pointer & switch fallthrough 详解和实战](https://juejin.cn/post/7072502044170387492)

## 流程控制

[# go if判断和for循环实战 goto使用的那些坑](https://juejin.cn/post/7069549500649439245)

## 函数

[# Go 函数详解 func 匿名函数 闭包](https://juejin.cn/post/7073279289101123614)

## ORM

[# Go 语言中操作 MySQL 数据库](https://juejin.cn/post/7103531271803912199)
作者：[# 宇宙之一粟](https://juejin.cn/user/3526889034751639)

[# golang 基于 mysql 实现分布式读写锁](https://juejin.cn/post/7147214210324234271) 作者：[# 二牛QAQ](https://juejin.cn/user/2344623087289965)

## 部署

[# 如何优雅的通过Shell脚本一键部署GO项目到服务器](https://juejin.cn/post/6943843305750970399)

## 扩展包

[# Go时间包jsontime深入浅出 如何优雅的对时间进行格式化 ｜Go 主题月](https://juejin.cn/post/6943897665960689678)

[# Go语言json包的使用技巧](https://juejin.cn/post/6945023713930641445)

[# Go 入门很简单：如何在 Go 中使用日志包](https://juejin.cn/post/7088342353638850567)
作者：[# 宇宙之一粟](https://juejin.cn/user/3526889034751639)

## 重要概念

[# Go开发web必懂的概念和底层原理，通过对比的方式让大家更好的理解 | Go主题月](https://juejin.cn/post/6950954283068031012)

# 进阶篇

## 协程

[# 什么时候用Goroutine？什么时候用Channel？](https://juejin.cn/post/6943952470993272845)

[# Goroutine就是协程：进程 线程 协程 各自的概念以及三者的对比分析](https://juejin.cn/post/6950952506176471071)

## RPC
[# Go RPC入门指南1：RPC的使用边界在哪里？如何实现跨语言调用？](https://juejin.cn/post/6946452659159171102)

## 反射

[# Golang的反射reflect深入理解和示例](https://juejin.cn/post/6844903559335526407) 
作者：[吴德宝AllenWu](https://juejin.cn/user/1187128287436808)

[# Go语言中的反射](https://juejin.cn/post/7097534989029343246)
作者：[任沫](https://juejin.cn/user/184373685261719)

## interface

[# Golang interface接口深入理解](https://juejin.cn/post/6844903555141222407)
作者：[吴德宝AllenWu](https://juejin.cn/user/1187128287436808)

## 错误处理

[# Go函数并发情况的错误处理](https://juejin.cn/post/7114970981872959525)
作者：[Masters](https://juejin.cn/user/1239904847411406 "https://juejin.cn/user/1239904847411406")

## 并发安全

[# Go源码解读-sync.Map的实现](https://juejin.cn/post/7068192854761275429)
作者：[Masters](https://juejin.cn/user/1239904847411406 "https://juejin.cn/user/1239904847411406")

## 部署

[# Go打包 部署 优雅的把Go项目部署到Linux服务器](https://juejin.cn/post/6954309251892248612)

## 规范&技巧

[# Go语言中比较优雅的写法 | 硬核！](https://juejin.cn/post/7082536852590166029)

[# 爆肝分享两千字Go编程规范](https://juejin.cn/post/7086094606856618014)

[# Go开发技巧和踩坑分享 | 代码结构 调试技巧 配置文件 元数据](https://juejin.cn/post/7102605823003590692)

# Go对比PHP/JAVA/C

[# Java VS Go 还在纠结怎么选吗，(资深后端4000字带你深度对比)](https://juejin.cn/post/7118866795418615822)
作者：[TodoCoder](https://juejin.cn/user/2472125987040093)

[# 为什么我觉得GoFrame的garray比PHP的array还好用？](https://juejin.cn/post/7105012753210802213)

[# GoFrame gset使用入门 | 对比PHP、Java、Redis](https://juejin.cn/post/7105231214390280200)

[# 如何在 Go 代码中运行 C 语言代码](https://juejin.cn/post/7077843585088897037)
作者：[# 宇宙之一粟](https://juejin.cn/user/3526889034751639)

# 好用的扩展包

[# GO语言框架中如何快速集成日志模块](https://juejin.cn/post/7119390985863299085)
作者：[Masters](https://juejin.cn/user/1239904847411406)

[# Go Web 编程入门：Go pongo2 模板引擎](https://juejin.cn/post/7102001354654089223)
作者：[# 宇宙之一粟](https://juejin.cn/user/3526889034751639)

[# 使用 Gorilla Mux 和 CockroachDB 编写可维护 RESTful API](https://juejin.cn/post/7120256019225116679)
作者：[# 宇宙之一粟](https://juejin.cn/user/3526889034751639)

# 设计模式

[# golang 设计模式-单例模式](https://juejin.cn/post/7124720007447052302)
作者：[# 二牛QAQ](https://juejin.cn/user/2344623087289965)

# 框架篇

## 学哪个框架？

[# Go主流框架对比：Gin Echo Beego Iris](https://juejin.cn/post/7067347764899741709)

[# 非常适合PHP/JAVA同学使用的GO框架：GoFrame](https://juejin.cn/post/7075098594151235597)

[# 12个值得一看的Go开源项目/框架](https://juejin.cn/post/7119348879820554247)
作者：[ReganYue](https://juejin.cn/user/3008695929418318)

## Gin框架&中间件

[# Go gin框架封装中间件之1：用户角色权限管理中间件](https://juejin.cn/post/6943147832937447431)

[# Go gin框架封装中间件之2：操作日志中间件](https://juejin.cn/post/6943503384729583652)

## GORM

[# Go GORM是时候升级新版本了 2.0新特性介绍（1）](https://juejin.cn/post/6945404499850854408)

[# Go GORM是时候升级新版本了 2.0新特性介绍（2）| Go主题月](https://juejin.cn/post/6946012224573931528)

## Echo

[# 回声嘹亮 之 Go 的 Echo 框架指南 —— 上手初体验](https://juejin.cn/post/7068555737756073997)
作者：[# 宇宙之一粟](https://juejin.cn/user/3526889034751639)

## Beego

[# go-web框架-beego的使用](https://juejin.cn/post/7121536082151211022)
作者：[# jy白了个白](https://juejin.cn/user/3421335915080093)

## GoFrame

### 数据结构

[# 为什么我觉得GoFrame的garray比PHP的array还好用？](https://juejin.cn/post/7105012753210802213)

[# GoFrame garray使用实践](https://juejin.cn/post/7090901734247104548)

[# GoFrame gset使用入门 | 对比PHP、Java、Redis](https://juejin.cn/post/7105231214390280200)

[# GoFrame gset使用实践 | 交差并补集](https://juejin.cn/post/7105572330612457486)

[# GoFrame gset使用技巧总结 | 出栈、子集判断、序列化、遍历修改](https://juejin.cn/post/7106013158279479327)

[# GoFrame glist 基础使用和自定义遍历](https://juejin.cn/post/7101515355062796296)

[# GoFrame gmap详解 hashmap、listmap、treemap使用技巧](https://juejin.cn/post/7101797623484383246)

[# GoFrame gtree 使用入门 | 养成读源码的好习惯](https://juejin.cn/post/7106458930057855013)

### 类型转换

[# GoFrame代码优化：使用gconv类型转换 避免重复定义map](https://juejin.cn/post/7081078067682082823)

### 通用变量

[# GoFrame 通用类型变量gvar | 对比 interface{}](https://juejin.cn/post/7106712908326764552)

### 数据校验

[# GoFrame数据校验之校验对象 | 校验结构体](https://juejin.cn/post/7110222819631464485)

[# GoFrame数据校验之校验结果 | Error接口对象](https://juejin.cn/post/7110952333193773064)

[# GoFrame如何实现顺序性校验](https://juejin.cn/post/7113360526410776583)

### 错误处理

[# GoFrame错误处理的常用方法&错误码的使用](https://juejin.cn/post/7112428421392629773)

### 上下文

[# GoFrame 如何优雅的共享变量 | Context的使用](https://juejin.cn/post/7113118741776793636)

[# Go 并发编程基础：什么是上下文](https://juejin.cn/post/7123200814402764831)
作者：[# 宇宙之一粟](https://juejin.cn/user/3526889034751639)

### ORM

[# GoFrame ORM 使用实践分享](https://juejin.cn/post/7082278651681013773)

[# GoFrame ORM原生方法 开箱体验 （上）](https://juejin.cn/post/7089980894525521957)

[# GoFrame ORM原生方法 开箱体验 （下）](https://juejin.cn/post/7090358951501365278)

[# GoFrame必知必会之Scan：类型转换](https://juejin.cn/post/7084569454956249101)

### 缓存管理

[# GoFrame 如何优雅的缓存查询结果](https://juejin.cn/post/7109465768445607967)

[# GoFrame gcache使用实践 | 缓存控制 淘汰策略](https://juejin.cn/post/7107986667293638663)

[# GoFrame gredis 配置管理 | 配置文件、配置方法的对比](https://juejin.cn/post/7108272085452980261)

[# GoFrame gredis 硬核解析 | DoVar、Conn连接对象、自动序列化](https://juejin.cn/post/7108698563328081928)

[# GoFrame gredis 如何优雅的取值和类型转换](https://juejin.cn/post/7109092852101021704)

### 协程管理

[# GoFrame gpool 对象复用池 | 对比sync.pool](https://juejin.cn/post/7102979667925139463)

[# goFrame的gqueue详解 | 对比channel](https://juejin.cn/post/7103502362429358116)

[# grpool goroutine池详解 | 协程管理](https://juejin.cn/post/7104661248213516319)

### 避坑指南

[# GoFrame避坑指南和实践干货](https://juejin.cn/post/7081959981456556068)

[# GoFrame避坑指南和实践干货（2）](https://juejin.cn/post/7085730973836378126)

### 性能测试

[# GoFrame grpool性能测试 | 对比原生goroutine](https://juejin.cn/post/7110510747498594341)

### 调试&单元测试

[# Go本地测试 如何解耦 任务拆解&沟通](https://juejin.cn/post/7111325551549218823)

[# Go Web 编程入门： 一探优秀测试库 GoConvey](https://juejin.cn/post/7115009937847091214)
作者：[# 宇宙之一粟](https://juejin.cn/user/3526889034751639)

# 应用实践

[# gtoken替换jwt实现sso登录 | 带你读源码](https://juejin.cn/post/7099449898529095717)

[# gtoken替换jwt实现sso登录 | 排雷避坑](https://juejin.cn/post/7102389025050361864)

[# Go对接三方API实践](https://juejin.cn/post/7083479769878102030)

[# Go一分钟对接ElasticSearch实践](https://juejin.cn/post/7084235852921962503)

[# 瞄一眼clickhouse(附 go demo)](https://juejin.cn/post/7068192828790145060)
作者：[Masters](https://juejin.cn/user/1239904847411406 "https://juejin.cn/user/1239904847411406")

# Git

[# Git使用实战：多人协同开发，紧急修复线上bug的Git操作指南。](https://juejin.cn/post/7018771333173477383)

[# Git 重命名远程分支 | 操作不规范，亲人两行泪。](https://juejin.cn/post/7104258964732575775)

# 刷题

如果你是学生党，没有机会接触商业项目，不用难过。刷力扣是个非常好的选择！

[用Go语言刷力扣专栏](https://juejin.cn/column/7070334316957401125)

为了方便大家刷Go语言的知识点，特意整理了面试题相关的文章：

[# 【狂刷面试题】GO常见面试题汇总](https://juejin.cn/post/7131717990558466062)

# 一起学习

公众号：程序员升级打怪之旅

微信号：wangzhongyang1993
