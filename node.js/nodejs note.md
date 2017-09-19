# 第一章：简介

* node.js基于ChromeV8引擎的javascript运行环境 

* node.js API分为全局对象 普通模块

* inux中使用git仓库：

### 进入git

* cd /wd/tools

* 创建一个：touch a   添加：git ad

* git st     git ci -m "add a"

### 01-hello.js 脚本文件

* 开头需注释#/usr/bin/node 加入到脚本文件中

* 退出 vim 输入chmod u+x 01-hello-world.js(指示在这个文件中有node解释)

* 每次运行只需要输入文件名即可

* 再创建新的脚本文件可以使用cp

### 02-hello-server.js  创建服务器脚本文件

* 用vi编辑器编写代码   编写好后  启动服务器

* 在浏览器上输入ip地址即可打开网页

* 打开防火墙：sudo firewall-cmd --permanent --add-port=8080/tcp

***********

# node.js API使用

# 第二章：全局：路径变量 

### 1.使用全局路径变量和文件变量

* （当前使用的脚本文件路径）file_name: /home/wangding/nodejs-demo/02-global-var/01-file-dir-name.js

* （当前使用的脚本所在的目录路径）dir_name: /home/wangding/nodejs-demo/02-global-var

* 通常用拼接字符串的方式写路径

# 第三章：全局：控制台

### 1.控制台 console.log

* ./01-format.js >msg.txt 命令行重定向

* cat err.txt 打开err.txt文件

### 2.基准时间测试：

* console.time('GET-DATA')  //括号里是一个标记表明测试的是一个什么任务

//测试的代码

* console.timeEnd('GET-DATA')  //结束代码

# 第四章：全局：进程

### process对象用法

* process 代表当前进程

* process.argv 属性返回一个数组，这个数组包含了启动Node.js进程时的命令行参数。第一个元素为process.execPath。如果需要获取argv[0]的值请参见     　process.argv0。第二个元素为当前执行的JavaScript文件路径。剩余的元素为其他命令行参数。

* eval() 函数可计算某个字符串，并执行其中的的 JavaScript 代码。

* childprocess代表启动的其他进程

* process.stdin.resume();  //进程会保持不自动退出(ctrl+C 退出进程)

1. (1)!bash

2. (2)ps aux 查看当前系统中的进程

3. (3)exit


* 命令：node -v (当前Node版本号) 对应console.log(node.version)

* whoami(当前用户) 对应console.log（process.getuid()）

* id()组ID console.log(process.getgid())

* pwd(当前文件路径) console.log(process.cwd())



### 内存数据

* 常驻内存大小：console.log(process.memoryUsage().rss);

*　V8动态分配堆得大小(总共)

* console.log(process.memoryUsage().heapTotal);

* V8已使用堆得大小

* console.log(process.memoryUsage().heapUsed);

* V8管理的绑定到C++对象上的内存

* console.log(process.memoryUsage().external);

### 命令：env环境变量

* 使用命令行参数  process.argv

* 命令：echo $? 查看退出码

* process.argv[2]是退出吗

### 标准输入：

* process.stdin返回一个对象，表示标准输入。

* slice() 方法可从已有的数组中返回选定的元素。

### 接受消息：

* process.on(事件处理方法)

### 发送消息：

* 1.命令行命令：ctrl+c ctrl+z

* 2.kill -2(-20)  + 进程 id

* 3.编写kill脚本发消息

# 第五章：全局：定时器

### 使用setTimeout 延迟执行任务

* 使用延迟执行通常用来模拟真实的异步操作

* 清楚定时器：三种方法：
1. 使用一个延迟执行任务，当到达某个时间就清楚定时器。
2. 在内部设置一个变量，将这个变量计数，计到某个数字的时候清楚定时器。
3. 调用timeID.unref(); 这个定时器会在很长一个任务（耗时操作）后自动清楚定时器。

# 全局：Buffer

###  Buffer 的基本使用方法

* buffer初始化的三种方法：
1. 使用数组的方法初始化：~ var array=['a',0xba,0xab]; buffer=new Buffer(array); ~
2. 直接初始化：~ var buffer=new Buffer("hello world!", "utf8");   ~ 注意   ：使用buffer.toString()的方法输出utf8格式
3. copy：~ buffer1=new Buffer(buffer2.length) buffer2.copy(buffer1,0,0,buffer2.length)  ~

* 使用buffer进行编码转换  var buf=new Buffer(x); console.log('user name and passwd',buf.toString('base64'));



