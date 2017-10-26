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

# 全局：Buffer（处理二进制数据流）

###  Buffer 的基本使用方法

* buffer初始化的三种方法：
1. 使用数组的方法初始化：`` var array=['a',0xba,0xab]; buffer=new Buffer(array); ``
2. 直接初始化：`` var buffer=new Buffer("hello world!", "utf8");  `` 注意   ：使用buffer.toString()的方法输出utf8格式
3. copy：`` buffer1=new Buffer(buffer2.length) buffer2.copy(buffer1,0,0,buffer2.length)  ``

* buffer填充方法：fill()

* 把字符串转化成另一种编码格式用的方法是什么？ toString('codingName');

*　从网页上获取一个位图　在命令行输入：wget URL

* 位图二进制文件格式:头信息+数据部分

* 使用buffer进行编码转换  var buf=new Buffer(x); console.log('user name and passwd',buf.toString('base64'));

* sz 文件名 可以将文件从linux上放到windows上

# 全局：模块管理

### require() 引用模块,export 暴露模块接口,module 代表当前模块

### npm ：缩写于 Node Packaged Modules,是node.js的模块管理器

* 安装第三方模块：npm install date-now 安装now模块

### 使用node.js全局模块

### 自定义模块

1. 编写模块JS代码:使用module.exports将这个模块暴露

2. 在主程序中引入模块,var pi=require('./02-export-var');

### 加载一组模块

1. 编写一个export-all.js 通过这个文件将几个模块关联起来

2. 在主程序中只需要引入export-all.js即可

* node.js 中的顶层对象是 global  前端中的顶层对象是window

# EventEmitter

## 两种类的继承方式

1. EventEmitter原型继承方式 

2. EventEmitter util继承  util.inherits(类名，events.EventEmitter);



# 第六章 文件操作(fs)

## fs.statSync() 同步的stat(2),返回一个stat数组对象    fs.statSync(src).isFile() //判断是不是文件 fs.statSync(src).isDirectory() //判断是不是文件夹

### 文件读取操作（cat命令的实现）

* 同步操作 process.argv[2]  //获取命令行参数  fs.openSync(file,'r');//打开文件 fs.readSync(fid,buf,0,len,0) //读取文件 fs.closeSync(fid) //关闭文件

* 异步操作 （高级API） fs.readFile(file,function(err,buf){}); 

* 同步操作 （高级API） fs.readFileSync(file).toString('utf8');  返回值是一个buffer

* 底层API和高级API混合

* 流的方式  fs.createReadStream(file).pipe(process.stdout);

### 文件操作

* 拷贝的实现（cp命令） 流的方式实现  fs.createReadStream(src).pipe(fs.createWriteStream(dst));

* 创建一个新的文件（touch命令） 写一个空文件 fs.writeFileSync(file,'');

* 修改一个文件的名称（mv命令） fs.renameSync(file1,file2);

* 删除文件（rm命令） fs .unlinkSync(file);

* 创建一个文件夹的命令（mkdir命令） fs.mkdirSync(file);

* 查看文件目录的功能(fs命令) fs.readdirSync(file);

* 删除文件目录的功能（rm -rf） fs.rmdirSync(file);

* 创建链接（ln file file1.lnk 硬链接  软链接(符号链接) ln -s file file1.lnk） fs.linkSync(file1,file2) fs.symlinkSync(file1,file) 

* 查看符号链接的链接指向 fs.readlinkSync(file);

* 修改文件所有者（chown） fs.chownSync(file,Number(uid),Number(gid))

* 修改文件权限（chmod） fs.chmodSync(file,number)

* 查看文件详细信息（stat） fs.statSync(file)

### 监视文件的内容

* var w=watch(目录，console.log); 监视某个目录的文件的改变，并打印到控制台上

* w.close(); 停止监视    

* ps aux |grep watch 查看当前的进程

### 文件的递归操作

* var join=require('path').join; //用于合并文件路径   join(folder,files[i]);

# 第七章 网络：分布式应用基础

# 第八章 子进程：执行外部程序

1. TCP协议：net
2. UDP协议：dgram
3. HTTP协议：http
4. DNS服务：dns

### net  var server=require('net').createServer();

*   connection事件 当新的connection建立时触发，socket是一个net.socket的实例对象   socket.remoteAdddress   ，有一个data事件

* Telnet（可以模仿浏览器，邮箱,ftp客户端与它们通信） 现在多用于网络服务测试    quit 退出  

### http(基于tcp)
* curl 服务器地址  

* var server=require('http').createServer();

* server.on('request',function(req,res){
})

* GET方法 http.get(url,function(res){})  状态码：res.statusCode  状态信息:res.statusMessage http版本：res.httpVersion http头：res.headers

* POST方法 http.request()

* DNS(nslookup 查询dns)  dns.lookup(ns,function(err,addr));

# web应用

##  http响应的完整信息包括四部分：状态行，响应头部字段列表，空行，响应主体

### 状态码

* 1xx 基本信息

* 2xx 成功信息

* 3xx 重定向

* 4xx 客户端错误
      
* 5xx 服务器错误

## http响应四部分：请求行，请求头部字段列表，空行，请求主体
