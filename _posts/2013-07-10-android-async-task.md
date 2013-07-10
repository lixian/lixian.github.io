---
layout: post
title: (Android) AsyncTask奇怪的参数泛型
---

## 参数泛型很奇怪
AsyncTask有一个奇怪的接口 `task.execute(Params... params)`

比如说下载一个url, 可以这样写

    new Task().execute(url);

但是这样写很容易让人产生歧义，以为是为了重用task

    Task task = new Task();
    task.execute(url);
    task.execute(url2);

上面的写法是错误的，在[Javadoc](http://developer.android.com/reference/android/os/AsyncTask.html)里面指明了
>   The task can be executed only once (an exception will be thrown if a second execution is attempted.)

这里可变参数是为了`new Task().execute(url, url2);` 不过大部分时间，可能只需要一个参数，这种写法很常见

    @Override
    protected String doInBackground(String... params) {
        String url = params[0];
        return download(url);
    }

那如果谁不小心写了`new Task().exec();`就会抛NPE了。
这样的话，是不是需要处理，把问题留给运行时？其实这本来应该是编译期的任务。
而且用户调用params的时候，没有多余的提示（参数名固定成了params，本来可以更具体一些的提示比如说urls）。

## 为什么不用构造函数

而相比之下，把参数放到构造函数里面，就没有这些问题

-   少一个泛型，简洁了不少，对新人来说，光理解这三个泛型就得花点时间了
-   没有歧义，没有参数从感觉上就是用一遍就扔的货
-   构造函数里面有变量名提示，否则可能每次都得去看doInBackground的注释了
-   对多类型参数的支持，不一定所有参数都是同一种类型。
    最开始用AsyncTask的时候，还在纠结，Param放哪些，构造函数放哪些
-   即使你想支持可变参数，也可以加到构造函数里面`public Task(String url, String ... others)`


## 结论

目前还没有看到用参数的好处，所以我自己定义了一个子类，把参数干掉

    public abstract class AsyncTaskVoid<Progress, Result> extends AsyncTask<Void, Progress, Result> {
        @Override
        protected abstract Result doInBackground(Void... params);
    }

