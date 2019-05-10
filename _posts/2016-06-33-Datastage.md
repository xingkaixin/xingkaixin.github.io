---
layout:     post
title:      Datastage
subtitle:   Datastage
date:       2016-06-03
author:     XingKaiXin
catalog: true
tags:
    - Datastage
    - ETL
---

### 什么是ETL
从数据源中抽取数据（Extraction），然后对这些数据进行转化（Transformation），最终加载（Loading）到目标数据库或数据仓库中去，这就是我们通常所说的“ETL过程”，它是数据整合的核心内容
#### ETL之前要对源数据作数据内容分析
- 数据内容格式、类型、长度，不同的字符集等
- 收集商业逻辑，了解客户的需求，从而觉醒ETL的策略
#### 脏数据的清洗
- 数据的完整性和一致性
### 传统ETL方法的弊端
- 需要手工编写大量的代码，费时费力
- 难以扩展、维护费用高
- 需要不断调整代码来符合需求的变化
- 对于不同的源和目标需要分别编写抽取和加载的代码
- 难以对元数据进行管理
### ETL工具的优点
- 图形化的界面，易于理解和操作
- 大数据处理能力强
- 能够处理多种文件形式的数据
### 常见的ETL工具
- IBM公司的DataStage
- Informatica
- SAP Data Integrator



### 什么是DataStage
#### DataStage是一套完成高效的专业数据整合工具。它可用于
- 数据仓库（Data Warehouse）
- 数据集市（Data Mart）
- 系统迁移（System Migration）
#### 通过DataStage
可以对ETL过程进行方便的管理
通过图形化的界面设计作业，对数据进行抽取、转换和加载。
可以对作业的执行进行调度和监控
使用内建的本地Repository，可方便的导入、导出和管理数据（Metadata）
#### 出色的数据源连接能力
ETL工具的数据源连接能力是非常重要的，这是直接决定它能够应用的范围。DataStage能够直接连接非常多的数据源，包括：文本文件，XML文件，企业应用程序等；几乎所有的数据库系统，比如DB2、Oracle、MS SQL Server、Informix等
### DataStage的体系结构及其组件
- DataStage的开发环境基于C/S模式
- Client只能安装在Windows平台上面
- Server支持多种平台，如Windows、Redhat Linux、AIX、HP－UNIX等。
- DataStage Client有四种客户端工具，分别是
- DataStage Administrator 设置服务器，添加删除工程，设置工程属性等。
- DataStage Manager 导入元数据，备份工程
- DataStage Designer 设计、编译、执行Job
- Director 执行、调度Job，检查、监控Job的运行状态
### 如何使用DataStage完成工作
- DataStage客户端工具连接到DataStage Server上进行ETL Job开发，DataStage Server再与后台的数据库连接起来进行数据处理
- DataStage的客户端工具之间是相互合作的关系
### ETL Job开发流程
- 用DataStage Administrator 新建项目，并对项目的属性进行设置
- 用DataStage Designer连接到新建的项目上进行图形化的ETL Job的设计
- 用DataStage Director来监控Job的运行日志，对设计好的ETL Job设置运行计划，比如多长时间运行一次ETL Job
- 用DataStage Manager进行ETL Job的备份，管理元数据等
### DataStage Administrator
### DataStage Designer and Manager
- 导入表定义
- 备份工程
- 导入备份工程
- 图形化、拖拽式的创建、删除、编辑Job，对Job进行编译和运行
### DataStage Director
- 对Job进行调度
- 监控、记录Job运行的log
### DataStage并行处理机制
#### 管道式数据处理
- 流水线式的数据处理过程
- 转换、清洗和加载同时进行
- 在数据处理过程中数据不落地，减少I/O开销
- 保持处理器始终被使用
### 分区算法（Partition Parallelism）
#### 数据被分为多个子集（subsets）进行处理
这些子集被称为“分区”（节点nodes）
#### 对每个分区里的数据都进行相同的操作
例如：对数据进行过滤操作时，每个分区都会按照相同的方式对数据进行过滤
#### 可以达到接近线性的扩展
假设数据在每个节点上时均匀分布的
8个处理器快8倍
24个处理器快24倍
### 常用Stage介绍
#### Sequential file stage
适用于一般顺序文件（定长或不定长），可识别文本文件或IBM大机EBCDIC文件
可作为数据源或目标
#### Data Set Stage
- DataSate内部文件格式，扩展名ds
- .ds文件保存元数据和分区信息，但不包括数据本身
- 以二进制存储，无法被外部程序读取
- 数据在DataStage读写时不需要进行转换，效率最高
- 可作为数据源或目标
#### Transformer stage
- 功能非常强大的Stage
- 需要C＋＋编译器的支持
- 有一个input link，多个output link
- 可以设置stage变量简化代码
- 可以对字段进行转换、判断
- 可以通过约束来指定符合条件的数据输出到哪个output link
- 可以使用自带的多种函数对数据进行处理、转换
- 在开发过程中可以使用拖拽对字段进行Mapping
- 可以在Mapping过程中对输出的字段进行增添或删减
#### Copy Stage
- 可以有一个输入，多个输出。它可以在输出时改变字段的顺序，但是不能改变字段类型。
- 当只有一个输入及一个输出时最好将Force设置为True，这样可以在Designer里看到运行结束，否则将无法标示运行结束，但不悔影像运行结果数据
#### Filter Stage
- 只有一个输入，可以有多个输出。根据不同的筛选条件，可以将数据输出到不同的output link
#### Funnel Stage
- 将多个字段相同的数据文件合并为一个单独的文件输出
- Continuous Funnel 从每一个input link中循环取一条记录
- Sort Funnel 按照Key值排序合并输出
- Sequence 先输出第一个input link的数据，输出完毕后再输出第二个input link的数据，以此类推，直到结束（可以通过调整link ordering调整输出顺序）
#### Lookup Stage
- 把数据读入内存执行查询操作，将匹配的字段输出，或者在符合条件的纪录中修改或加入新的字段
#### Join Stage
- 将多个表连接后输出，连接方式为：Full Outer，Inner ，Left Outer，Right Outer
#### Join Stage和Lookup Stage对比
- Join stage将多个表的字段连接起来输出结果
- 输入的数据分为主Link和辅Link，它们之间必须要有相同的Key字段进行关联
- 特点：对所有主、辅表数据量都非常多，且数量级相差不大的情况下使用
- Lookup stage功能与Join Stage蕾丝，都分为主表与辅表，通过关键字段匹配，然后取出需要的数据
- Lookup允许有一条reject link，将lookup失败的数据输出到其他stage
- Lookup允许有四种处理方式：Continue、Drop、Fail、Reject
- 允许返回多条匹配上的纪录（join只能返回一条）
- 特点：不对数据进行排序，而是将辅表中的所有数据装入内存，再与主表中每一条数据进行匹配
- 在辅表数据记录远少于主表的情况下适用，且辅表数据量不能太大，以确保能够全部装入内存
#### Sort stage
功能说明：只能有一个输入及一个输出。按照指定的Key值进行排序。可以选择升序还是降序，是否允许去除重复的数据（只能保留第一条）
#### Remove Duplicates stage
功能说明：去除按照key字段排好序的数据中key值重复的纪录，通常与sort stage配合使用，可选择保留重复纪录的第一条还是最后一条
#### Row Generator stage
按照给定的条件生成伪数据，一般用于测试
#### Peek stage
显示各字段的数据内容，可控制显示的纪录数量，并且按分区编号显示数据，可以选择结果输出到Job log或output到文件，在开发job的过程中十分有用，可以作为job开发过程中的临时数据终点，以便检查数据的正确性
