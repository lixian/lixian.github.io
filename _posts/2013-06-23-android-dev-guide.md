---
layout: post
title: Android开发入门
---

记录Android开发的常见问题和解答，欢迎补充（学习碰到的问题，可以在这里先记录下来）

## 开发工具

### IDE

之前用Eclipse的，可以直接用ADT（Eclipse集成Android环境），不过我推荐使用Android Studio（Intellij IDEA），而且有了Google的支持，以后只会更好用。

### 开发API版本

使用SDK的Api版本，建议使用最新的。
因为学习安卓很大方便的优势，就是开源。而Android源码更新速度非常快（特别是最新的版本）。很多老旧的代码会重构的更清晰，文档更全。官方的文档，也是从最新版本编译过去的。所以从学习的角度，也应该看最新的源码。

可以把targetSdkVersion设置为较高版本Api，而设置minSdkVersion为兼容版本Api。

### 开发机（手机设备）
AVD可以用，但是跟IOS的虚拟机体验差太远了，只能做辅助。

理论上任何设备都可以做开发机，但是安卓的版本最好用最新的。
直接用旧的手机开发，有一些问题

-   比如说屏幕出现卡顿，你无法判断是机器性能差，还是App性能相关的Bug。
    这会让你对卡顿麻木，从而隐藏一些Bug（你会把所有的卡顿都当成是手机性能问题）。
    当然也有可能机器性能太好隐藏了不太致命的Bug，这个需要权衡一下。

-   没法尝试最新的Feature。即使目前的项目用不上，也应该有所了解，这可以[使你领先竞争对手](http://www.youtube.com/watch?feature=player_embedded&v=GcNNx2zdXN4)。

-   害怕之后会出现兼容性问题，直接用最旧的系统来开发。
    有利有弊吧，为了之后的兼容性而影响开发产品Feature速度 ，感觉因小失大。
    这个可以放到后面考虑，Android发展很快的，努力向前看，否则就想想塞班吧。

-   不流畅很影响开发人员的体验，而开发是前期用这个App最多的人。让开发用的爽，开发才会更有动力去做好。

推荐使用最新的Google Nexus系列或者三星较新的手机。
向公司申请，如果公司不太方便的话，就自己买一台吧，Android设备还是比较便宜的。

## 学习资源

-   developer.android.com
-   google & stackoverflow.com
-   source code & samples
-   [Android开发者必知的开发资源](http://www.importnew.com/3988.html)
-   [最受欢迎的开源项目](http://www.csdn.net/article/tag/%E6%9C%80%E5%8F%97%E6%AC%A2%E8%BF%8E%E7%9A%84%E5%BC%80%E6%BA%90%E9%A1%B9%E7%9B%AE)
-   [An Android Tutorial](http://www.vogella.com/articles/Android/article.html)
-   本公司其他组的手机项目，好处就是你可以直接和本人交流。

初学安卓，我自己感觉比较重要的几点

-   和公司其他Android开发搞好关系，目前有道的手机开发人员还是属于各个产品，交流较少，可以考虑跨组。 如果能直接和技术大牛交流的话，成长会快很多。

-   跟紧Google步伐，了解开源最新动向。比如说最近出了什么开源工具等等应该了解。
推荐[AndroidDev Weekly](http://androiddevweekly.com/)，每周更新的。

-   不看中文资料（除非你能确信作者特别牛逼）。 Android是一个发展很快的东西，而中文社区更新较慢，很容易误入歧途而浪费一些时间。 一开始看英文慢没问题，总比走错路强，而且我们还有最牛逼的有道词典。。。

-   把自己的手机语言调成英文。这样可以让你对一些手机元素的英文说法更了解，遇到问题也知道查什么关键字。

安卓开发门槛不高，但是贵在质量和速度（不影响质量的前提下），特别是对于一些小项目，这应该是核心竞争力。

## 问题和解答


