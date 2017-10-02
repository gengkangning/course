# 创建一个web服务器
` 
var http=require('http');
http.createServer(function(req,res){
  res.writeHead(200,{'Content-Type:'text/plain'})
  res.end('Hello World\n')
}).listen(1337,'127.0.0.1') `

createServer创建一个服务器，通过listen在1337端口监听请求，可以收到任何来自端口的请求，当请求进来，执行内部的匿名函数，req(请求体)：获取请求的相关信息（url,请求的类型是get还是post）,res(响应体):告诉服务器给这个请求响应一些内容

