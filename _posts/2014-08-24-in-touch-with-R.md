---
layout: post
title: 接触 R 语言
---

之前偶尔会遇到一些需求，整理一些数据。
比如说对两个 CSV 进行 merge，再做一些整理。

- a.csv 包括 id, info1
- b.csv 包括 id, info2
- 针对结果，取某些列出来

如果是数据库中两个表，进行 join 就可以得到。

    select a.id, a.info1, b.info2
    from a
    join b
    on a.id == b.id
    where ...

使用通用语言如 Java/Scala/Python，冗余代码很多，面对修改很无力。
如果导入数据库操作再输出，确实可以提高抽象层次，但是建表的操作有些冗余，有点杀鸡用牛刀的感觉。

## 统计语言
如果把问题划到统计领域，便可以高度抽象。 
一个偶然的机会接触到 R 语言，此类需求迎刃而解。 
如果没有听说过 R 语言，至少应该听说过 Excel 和 Matlab。这些都可以作为统计学工具。

- Excel，简单易用，偏重可视化操作和商用，编程能力弱，处理较大的数据比较麻烦，收费。
- Matlab，在学术领域很常见，有强大的矩阵支持，强大的图形化输出，收费。
- R，类似于 Matlab，开源，编程能力比较强且拥有大量第三方库，免费。

Java 基本类型一般是 Integer/String 等等。而在 R 里面，最基本的类型是 vectors，类似于 Java 中的 List； 而 Java 中的 Integer/String 等，则是长度为 1 的 vectors。

## 一个例子
通过一个例子，我们可以了解一下统计语言如何提高抽象层次。比如说要取 1 到 10 里面的奇数。在解释器里面我们可以输入
    
    > x <- 1:10
    > x[x %% 2 == 1]
    [1] 1 3 5 7 9

## 分步骤解析一下

    > x <- 1:10

`1:10` 是一个语法糖，生成一个序列。`<-` 是赋值操作。

    > x
     [1]  1  2  3  4  5  6  7  8  9 10

在解释器中直接输入变量名 `x`，显示其详情。

    > x %% 2
     [1] 1 0 1 0 1 0 1 0 1 0

这步有两个概念

-   Vectorization，`%%` 是取余，但是 R 的操作符一般是针对 vectors 的，依次对其中的每个元素进行操作。
-   Recycling，如果两个 vectors 长度不相等，会自动把短的循环补齐。

继续往下

    > x %% 2 == 1
     [1]  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE

`==` 同样是针对两个 vectors，并自动把短的补齐。

    > x[x %% 2 == 1]
    [1] 1 3 5 7 9    

Filtering，对 vectors 取子集，仅把其中位置为 `TRUE` 的元素取出来。

## 展开
R 的基本类型中除了 vectors, 最重要的便是 data.frame，类似于 SQL 中的一张表。R 的表达能力比 SQL 强很多，而且可以作为一个脚本语言使用，有较多的第三方包。

上面例子中，类似的概念在支持函数式编程的语言里面也有，如 map/filter 等等。 
但是对于 data.frame 的脚本级操作，通用语言很难达到同样的抽象层次。 
对于有相关统计需求的同学，与其在通用语言的泥潭里面怎么折腾都无法减小复杂度，不如尝试一下统计语言。

R 的杀手锏其实是其强大的图表输出能力，有兴趣的可以多了解一下，略过。

可以这么来理解 R，它并不是一门单纯的统计语言，而一个统计环境，其中包含了一个统计脚本语言，以及强大图表输出功能。

## 资料
-   [The Art of R Programming](http://book.douban.com/subject/6727873/)，作者有程序员背景，推荐码农从这本入手，基本类型讲清楚，其他的都好说。
-   [R in Action](http://book.douban.com/subject/6126331/)，这本书是统计学背景的人写的，例子很多，图表也很多。
-   [R programming for those coming from other languages](http://www.johndcook.com/R_language_for_programmers.html)，某 R 大牛 blog 上的一篇文章，看完了可以到处翻翻。
