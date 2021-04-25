# MapReduce、Spark、Storm

## MapReduce
    用于大规模数据集的并行计算。
&ensp;&ensp; &ensp;&ensp;
MapReduce 计划分三个阶段执行，
即 map 阶段，shuffle 阶 段，reduce 阶段。Map 映射，Reduce 化
简。Map 操作，对一部分原始数据进行指定操作，每个 Map 都针对
不同数据，Map 与 Map 之间相互独立。Reduce 操作，对每个 Map 
产生的 一部分中间结果进行合并，每个 Reduce 处理的 Map 中间
结果是互不交叉的，所有 Reduce 产生的结果经过简单连接形成完整
的结果集。   
&ensp;&ensp; &ensp;&ensp;MapReduce 是面向大数据并行处理的计算模型、框架和平台，它隐含了以下三层含义
  
### 1.MapReduce 是一个基于集群的高性能并行计算平台（ClusterInfrastructure）。

&ensp;&ensp;&ensp;&ensp; 它允许用市场上普通的商用服务器构成一个包含数十、数百至数千个节点的分布和并行计算集群。  

    
### 2.MapReduce 是一个并行计算与运行软件框架（Software Framework）。

&ensp;&ensp;&ensp;&ensp;它提供了一个庞大但设计精良的并行计算软件框架，能自动完成计算任务的并行化处理，自动划分计算数据和计算任务，在集群节点上自动分配和执行任务以及收集计算结果，将数据分布存储、数据通信、容错处理等并行计算涉及到的很多系统底层的复杂细节交由系统负责处理，大大减少了软件开发人员的负担。
  
### 3.MapReduce 是一个并行程序设计模型与方法（Programming Model & Methodology）。

&ensp;&ensp;&ensp;&ensp;它借助于函数式程序设计语言 Lisp 的设计思想，提供了一种简
便的并行程序设计方法，用 Map 和 Reduce 两个函数编程实现基本的并行计算任
务，提供了抽象的操作和并行编程接口，以简单方便地完成大规模数据的编程
和计算处理。

>MapReduce 提供了以下的主要功能：  
1）数据划分和计算任务调度。  
2）数据/代码互定位。  
3）系统优化。  
4）出错检测和回复。  

>MapReduce 设计上具有以下主要的技术特征：   
1)向“外”横向扩展，而非向“上”纵向扩展。  
2）失效被认为是常态。  
3）把处理向数据迁移。  
4）顺序处理数据、避免随机访问数据。  
5）为应用开发者隐藏系统层细节。  
6）平滑无缝的可拓展性。  

## Spark 
    Spark 是一个基于内存计算的开源集群计算系统，目的是更快速
的进行数据分析。
&ensp;&ensp;&ensp;&ensp;Spark 由加州伯克利大学 AMP 实验室 Matei 为
主的小团队使用 Scala 开发，类似于 Hadoop MapReduce 的通用并
行计算框架，Spark 基于 Map Reduce 算法实现的分布式计算，拥有
Hadoop MapReduce 所具有的优点，但不同于 MapReduce 的是 Job 
中间输出和结果可以 保存在内存中，从而不再需要读写 HDFS，因此
Spark 能更好地适用于数据挖掘与机器学 习等需要迭代的 Map 
Reduce 的算法。
Spark 的核心是建立在统一的抽象弹性分布式数据集 RDD，RDD 
本质上是一个只读的分区 记录集合。每个 RDD 可以分成多个分区，
每个分区就是一个数据集片段。一个 RDD 的不 同分区可以保存到集
群中的不同结点上，从而可以在集群中的不同结点上进行并行计算。
RDD 具有容错机制，并且只读不能修改，可以执行确定的转换操作创
建新的 RDD。RDD 的 操作分为转化（Transformation）操作和行动
（Action）操作。转化操作就是从一个 RDD 产 生一个新的 RDD，而
行动操作就是进行实际的计算。

### 特点

#### 1.运行速度快。
&ensp;&ensp;&ensp;&ensp;Spark 拥有 DAG 执行引擎，支持在内存中对数据进行迭代
计算。官方提供的数据表明，如果数据由磁盘读取，速度是 Hadoop MapReduce的 10 倍以上，如果数据从内存中读取，速度可以高达 100 多倍。  
#### 2.易用性好。
&ensp;&ensp;&ensp;&ensp;Spark 不仅支持 Scala 编写应用程序，而且支持 Java 和
Python 等语言进行编写，特别是 Scala 是一种高效、可拓展的语言，能够用简
洁的代码处理较为复杂的处理工作。  

#### 3.通用性强。Spark 生态圈即 BDAS（伯克利数据分析栈）包含了 Spark 
&ensp;&ensp;&ensp;&ensp;Core、Spark SQL、Spark Streaming、MLLib 和 GraphX 等组件，这些组件分别
处理 Spark Core 提供内存计算框架、SparkStreaming 的实时处理应用、Spark 
SQL 的即席查询、MLlib 或 MLbase 的机器学习和 GraphX 的图处理。  

#### 4.随处运行。Spark 具有很强的适应性，能够读取 HDFS、Cassandra、
&ensp;&ensp;&ensp;&ensp;HBase、S3 和 Techyon 为持久层读写原生数据，能够以 Mesos、YARN 和自身携
带的 Standalone 作为资源管理器调度 job，来完成 Spark 应用程序的计算。  

## Storm 
    Storm 是一个分布式的、可靠的、容错的流式计算框架。
&ensp;&ensp;&ensp;&ensp;
MapReduce 也不适合进行流式计算、实时分析，比如广告点击计
算等，而 Storm 则更擅长这种计算、它在实时性要远远好于
MapReduce 计算框架。Storm 一开始就是为实时处理设计，因此在实
时分析性能监测等需要高时效性的领域广泛采用。Storm 在理论上支
持所有语言，只需要少量代码即可完成适配。Storm 把集群的状态存
在 Zookeeper 或者本地磁盘，所以后台进程都是无状态的（不需要
保存自己的状态，都在 zookeeper 上），可以在不影响系统健康运行
的同时失败或重启。Storm 可应用于数据流处理、持续计算（持续地
向客户端发送数据，它们可以实时的更新以及展现数据，比如网站指
标）、分布式远程过程调用（轻松地并行化 CPU 密集型操作）
### 特点： 
#### 1.适用场景广泛。
&ensp;&ensp;&ensp;&ensp;Storm 可以实时处理消息和更新 DB，对一个数据量进行
持续的查询并返回客户端（持续计算），对一个耗资源的查询作实时并行化的处
理(分布式方法调用，即 DRPC），Storm 的这些基础 API 可以满足大量的场景。
#### 2.可伸缩性高。
&ensp;&ensp;&ensp;&ensp;Storm 的可伸缩性可以让 Storm 每秒可以处理的消息量达
到很高。扩展一个实时计算任务，你所需要做的就是加机器并且提高这个计算
任务的并行度。Storm 使用 ZooKeeper 来协调集群内的各种配置使得 Storm 的
集群可以很容易的扩展。
#### 3.保证无数据丢失。
&ensp;&ensp;&ensp;&ensp;实时系统必须保证所有的数据被成功的处理。那些会
丢失数据的系统的适用场景非常窄，而 Storm 保证每一条消息都会被处理，这
一点和 S4 相比有巨大的反差。  
#### 4.异常健壮。
&ensp;&ensp;&ensp;&ensp;Storm 集群非常容易管理，轮流重启节点不影响应用。  
  
#### 5.容错性好。
&ensp;&ensp;&ensp;&ensp;在消息处理过程中出现异常，Storm 会进行重试。
#### 6.语言无关性。
&ensp;&ensp;&ensp;&ensp;Storm 的 topology 和消息处理组件(Bolt)可以用任何语
言来定义，这一点使得任何人都可以使用 Storm