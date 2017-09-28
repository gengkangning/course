# nodejs简介

## nodejs是有很多模块构成的，使用require('http(等)')引入模块

* Node.js 是单进程单线程应用程序，但是通过事件和回调支持并发，所以性能非常高。

* Node.js 的每一个 API 都是异步的，并作为一个独立线程运行，使用异步函数调用，并处理并发。

* Node.js 基本上所有的事件机制都是用设计模式中观察者模式实现。

* Node.js 单线程类似进入一个while(true)的事件循环，直到没有事件观察者退出，每个异步事件都生成一个事件观察者，如果有事件发生就调用该回调函数

## 回调函数

* Node.js 异步编程的直接体现就是回调，

* 因此，阻塞是按顺序执行的，而非阻塞是不需要按顺序的，所以如果需要处理回调函数的参数，我们就需要写在回调函数内。

## Node 应用程序是如何工作的？

* 在 Node 应用程序中，执行异步操作的函数将回调函数作为最后一个参数， 回调函数接收错误对象作为第一个参数。


## 事件机制

* 绑定事件及事件的处理程序 eventEmitter.on('eventName', eventHandler);

* 触发事件 eventEmitter.emit('eventName');

### 监听事件步骤

1. //引入事件模块 
var events = require("events");

2. //创建事件监听的一个对象
var  emitter = new events.EventEmitter();

3.  //监听事件some_event
emitter.addListener("some_event",function(){
    console.log("事件触发，调用此回调函数");
});

4. //触发事件some_event
emitter.emit("some_event");

* 大多数时候我们不会直接使用 EventEmitter，而是在对象中继承它。包括 fs、net、 http 在内的，只要是支持事件响应的核心模块都是 EventEmitter 的子类。

# Nodejs Buffer(缓冲区)

* JavaScript 语言自身只有字符串数据类型，没有二进制数据类型。

* 但在处理像TCP流或文件流时，必须使用到二进制数据。因此在 Node.js中，定义了一个 Buffer 类，该类用来创建一个专门存放二进制数据的缓存区。

* 	buf.length length 是 buffer 对象所分配的内存数，它不会随着这个 buffer 对象内容的改变而改变。

# Node.js Stream(流)

* Stream 是一个抽象接口，Node 中有很多对象实现了这个接口。例如，对http 服务器发起请求的request 对象就是一个 Stream，还有stdout（标准输出）。

## Node.js，Stream 有四种流类型：

* Readable - 可读操作。
* Writable - 可写操作。
* Duplex - 可读可写操作.
* Transform - 操作被写入数据，然后读出结果。

## 所有的 Stream 对象都是 EventEmitter 的实例。常用的事件有：
* data - 当有数据可读时触发。
* end - 没有更多的数据可读时触发。
* error - 在接收和写入过程中发生错误时触发。
* finish - 所有数据已被写入到底层系统时触发。

