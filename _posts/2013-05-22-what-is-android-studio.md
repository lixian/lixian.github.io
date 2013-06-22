---
layout: post
title: 是时候抛弃Eclipse 转向IntelliJ了
---

2013年Google I/O大会，推出了新的Android集成IDE“Android Studio”，最大的转变就是从Eclipse切换到了IntelliJ IDEA。

## Google终于抛弃了Eclipse了
IDE是个大坑，不是谁想做就能做的，关键问题是做了也赚不了大钱。Google才不会吃力不讨好，搞Chrome可以给搜索带流量，搞Android能打击对手苹果，搞IDE能干啥？所以，Google需要只是一个集成的傻瓜包而已。让只有一个月Java基础的人，也可以直接下载了这一个傻瓜包，照着教程就能学习Android，而不是把大把的时候花在折腾插件上。

目标明确了，那剩下就是跟谁合作的问题。Eclipse开源，市场份额大，所以Google最开始和Eclipse合作，出了ADT傻瓜包。ADT说白了就是SDK+Eclipse+Android Plugin for Eclipse。但是Eclipse有个问题，太慢了，至少对于我来说。
也许是一些新的feature，Eclipse架构很难支持。不管怎么样，Google发现Eclipse没什么意思了，而IntelliJ这边发展不错，现在已经号称是最好用的Java开发环境了。

于是Google转身就投向了IntelliJ IDEA。对于IntelliJ来说，有Google带头的话，肯定会有大把的流量过来，辛苦了这么多年，终于算是熬到头了。

那Android Studio是什么？

[Is Android Studio a fork of IntelliJ IDEA?](http://blogs.jetbrains.com/idea/2013/05/intellij-idea-and-android-studio-faq/)<br/>
No. Android Studio and the Android plugin for IntelliJ IDEA are built from the same code, and all of the changes in Android Studio are, and will continue to be, available in IntelliJ IDEA releases.


根本不是新东西。Android Studio = SDK + Intellij + Android Plugin For IntelliJ。
Android Studio这个名字就是为了推广用，估计因为要开I/O大会，直接拿捆绑包上，有点不太好意思，总得有点新的东西吧。赶紧花时间给Android Plugin For IntelliJ攒几个新feature，这样也能赢点掌声。
至于新的命名，只是为了推广用。傻瓜包最好推。否则插件SDK啥的，得解释半天。

现在发现问题的本质了，发布Android Studio的意思就是，Eclipse没前途，G家要换到IntelliJ这边了（打脸）。

## 对于开发者来说（不仅仅是Android的开发者，而是Java开发者）
大家都做IDE这么多年了，互相抄一抄，特性上应该也差不了太多。至于用Eclipse还是IntelliJ，也不是什么太大的问题，主要的功能应该两者都有的。

但是，Eclipse实在是有些时候不太好用，最要命的，应该就是速度了，打开慢就不说了，大不了我永远不关机。最近我的Eclipse大约每隔半个多小时内存就爆到近1G，UI界面都会特别卡。JVM调优也尝试过，但是不是很简单就能解决问题的。我从32位换到64位，内存多了一些，还是卡，已经没有精力再去折腾了。
之前想换，但是切换熟悉的IDE，确实还是有成本的，一直都忍下来了。而且Intellij之前虽然听说过，但是老感觉是个小众IDE，有前途吗？谁都不想用一个没几年就会被关掉的产品，想想那些悲催的雅虎中国邮箱用户，对不对？

不过，现在有Google摇旗，Intellij肯定近一段时间会越发红火，虽然Google也不太靠谱，例如Google Reader，但是毕竟已经算是比较靠谱了。Android这块还是有利可图的，而且Intellij本行就是做IDE的，能赚到钱，自然也乐得继续维护下去。
与其继续忍受Eclipse的龟速开发，长痛不如短痛，换了。

对于Android开发者来说，是用Android Studio还是IntelliJ？
上面都说过了，是同一个东西，我现在用的Intellij Ultimate版本，30天试用期，到期了可以换社区版。正版的个人价是$199，不是给中国程序员定的，之前有社区搞过一个团购，只要150元，不过现在已经没了，等下次吧。

## 切换的成本
其实切换的成本，没有你想象的那么高，以后时间会补回来的。
这个是IntelliJ官方的QA，[for Eclipse Users](http://www.jetbrains.com/idea/documentation/migration_faq.html)

## 关于快捷键
一个IDE好用不好用，最重要的一块就是快捷键设计，之前一直很郁闷eclipse为什么连Preference都没有一个快捷键。换到IDEA，瞬间爽快了很多，几乎所有的常用操作都有快捷键，基本上可以做到纯键盘操作。

熟悉了一段时间IntelliJ的快捷键，发现其实IntelliJ快捷键，设计的比Eclipse要好。而且快捷键本来就是跟IDE特性息息相关的，IntelliJ的快捷键，是针对自己的特性，专门设计过的。我**不建议使用针对Eclipse的KeyMap**，花点时间熟悉Intellij的设计吧。

而且学习Intellij的快捷键，有很好的办法

1.  Alt菜单与鼠标右键，执行的时候，自然会提示快捷键。
2.  Help | Default Keymap Reference，这个是一个大的常用快捷键表，建议有空的时候，花点时间过一遍。
3.  Help | Find Action (Ctrl+Shift+A)，这个快捷键非常有用，是一个命令查找，在任何时间，都可以执行此命令，输入你需要的操作，例如”extract method”，下面会出现命令以及对应的快捷键
4.  这就要求你熟悉操作的英文名， 在Eclipse里面可能习惯了肌肉记忆，不太记得快捷健的英文名了。大不了去Eclipse里面找找，或者翻IDEA的Keymap表，有分类目录。

用了一段时间的IDEA之后，发现即使Eclipse现在不卡了，也换不回去了，有句老话叫做“由奢入俭难”。

最后再吐槽一句，开源且不赚钱的东西，一般仅仅都只是做到能用，就没动力继续做下去了。如果有商业公司伺候你的话，会让你觉得好用，仅仅能用很难让用户掏钱，要让用户爽。

