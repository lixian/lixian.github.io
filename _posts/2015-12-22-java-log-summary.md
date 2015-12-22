---
layout: post
title: Java Log 小结
---

## 最佳实践
slf4j 和 log4j 一起用，基本上已经是业界共识。

- slf4j 负责 API，业务代码中只应该出现 slf4j。
- log4j 负责实现，配置强大。

## FAQ
### Q: 项目里面已经使用了其他 log 框架了，怎么办？
如果是业务代码，直接修改代码换了就行了，一劳永逸。

如果是使用的开源框架没用 slf4j，可以使用 bridge 来替换原来的实现，[相关文档](http://www.slf4j.org/legacy.html)。
比如 Spring 因为遗留问题使用了 jcl，后面想换已经来不及了，官方推荐的解决方案就是[这样](http://spring.io/blog/2009/12/04/logging-dependencies-in-spring/)。
原理是直接把原来的 jar 包删除了，原地换一个新的实现(bridge)，把 log 转给 slf4j。确保整个 classpath 里面都没有相关的 jar 包 (不光 Spring 依赖进行的)，否则 ClassLoader 看到多个实现会很困扰。

### Q: 以下两条 log 语句有什么区别，应该选哪个？
```java
List<String> hitKeys = ...;
log.debug("Cache hit. Keys: " + hitKeys);   // string
log.debug("Cache hit. Keys: {}", hitKeys);  // format
```
A: 应该使用 format 格式。当不需要显示 debug 层级的 log 时，第一种会执行 toString()，而第二种不会。对于 List 来说，toString 是一个耗时的操作，应该尽量避免。

### Q: 如何更方便的生成 log 代码
A: 两种选择。

第一种，智能代码片段。

推荐插件 IDEA 的 log support plugin。强于普通代码片段的地方在于，会根据当前 class 是否存在 logger 进行智能的增加定义。

用法为直接在需要输入 log 的地方输入 `logi<tab>`/`logi<tab>`/...，即可自动选择
- 不存在 logger，根据配置好的框架及名称生成一个 logger，并打 log。

```java
private static final Logger log = LoggerFactory.getLogger(MyClass.class);
//....
log.info("<cursor>")
```
- 存在 logger，直接使用当前 logger 名称打 log，例如目前已经存在 LOG 的 logger

```java
LOG.info("<cursor>")
```

还可以配置不同的 log framework,包括 slf4j, log4j, android 等等，非常好用。

第二种，编译期代码生成
Lombok 的 [Log Annotation](http://projectlombok.org/features/Log.html)。在 Class 上加 `@Slf4j` 即可自动在编译后的代码中加入

```java
private static final Logger log = LoggerFactory.getLogger(LogExample.class);
```

因为已经有第一种了，加 annotation 太麻烦了，兼容性也有问题，不推荐。

### Q: 是否使用静态域
参考官网的解释 <http://www.slf4j.org/faq.html#declared_static>

