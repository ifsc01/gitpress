---
title: 面试 小记
date: 2020-6-2
---

## 基础

* tcp/ip 
* http 协议
  * http2/http3

📖
* 《HTTP权威指南》

## golang 

* golang gc 机制
  * https://draveness.me/golang/docs/part3-runtime/ch07-memory/golang-garbage-collector/
  * https://segmentfault.com/a/1190000018161588

* defer panic recover 
* make & new 的区别
  * channel map slice
* slice的坑
* for range 执行goroutine 的坑
* csp并发模型
  * goroutine & channel
  * csp vs actor
* golang 互斥锁 读写锁 WaitGroup

### GPM 调度模型
  - [Go 为什么这么“快”](https://zhuanlan.zhihu.com/p/111346689)
  - [深入golang runtime的调度](https://zboya.github.io/post/go_scheduler/)
  - [Go 语言调度器与 Goroutine 实现原理 | Go 语言设计与实现](https://draveness.me/golang/docs/part3-runtime/ch06-concurrency/golang-goroutine/)

### sync.Map 并发安全的map & 优化

* repo https://github.com/orcaman/concurrent-map
* 与单纯使用原生map和互斥锁的方案相比，使用sync.Map可以显著地减少锁的争用。sync.Map本身虽然也用到了锁，但是，它其实在尽可能地避免使用锁
* 并发安全字典如何做到尽量避免使用锁？ https://time.geekbang.org/column/article/42800

### net/http

  * http.Handle
* web framework
  * https://github.com/gin-gonic/gin
  * https://github.com/kataras/iris

## redis mysql 

* 索引原理和优化
  * [如何使用 EXPLAIN 查看 SQL 执行计划？](https://time.geekbang.org/column/article/126169)

* b+ 数
  * 索引的原理：我们为什么用B+树来做索引？
* Mongodb 为啥用 B树
* redis 数据结构
  * zset 跳表
* redis rdb & aof


## 必读文章

* [17 | 跳表：为什么Redis一定要用跳表来实现有序集合？](https://time.geekbang.org/column/article/42896)
- [24丨索引的原理：我们为什么用B+树来做索引？](https://time.geekbang.org/column/article/112298)
- [为什么 MySQL 使用 B+ 树 - 面向信仰编程](https://draveness.me/whys-the-design-mysql-b-plus-tree/)
- [为什么 MongoDB 使用 B 树 - 面向信仰编程](https://draveness.me/whys-the-design-mongodb-b-tree/)
- [为什么 Redis 选择单线程模型 - 面向信仰编程](https://draveness.me/whys-the-design-redis-single-thread/)

## leetcode 