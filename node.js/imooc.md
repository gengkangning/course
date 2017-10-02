# 创建一个web服务器
` 
var http=require('http');
http.createServer(function(req,res){
  res.writeHead(200,{'Content-Type:'text/plain'})
  res.end('Hello World\n')
}).listen(1337,'127.0.0.1') `

createServer创建一个服务器，通过listen在1337端口监听请求，可以收到任何来自端口的请求，当请求进来，执行内部的匿名函数，req(请求体)：获取请求的相关信息（url,请求的类型是get还是post）,res(响应体):告诉服务器给这个请求响应一些内容

# 模块

## 模块的分类：核心模块，文件模块，第三方模块

## 模块的流程：定义模块------标识--------引用

# api

## url

* url.parse('www.hao123.com') 这个地址的组成部分

* url.format({}) 将地址组成部分合成为一个地址

* url.resolve()

## querystring 用于字符串和对象的相互转换和字符串的转译。  JSON 是 JS 对象的字符串表示法，它使用文本表示一个 JS 对象的信息，本质是一个字符串。

## http 

### 流程 http客户端发起请求，创建客户端------http服务器在端口监听客户端请求----http服务器向客户端返回状态和内容


