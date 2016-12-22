#day 1

##慕课网学习node.js笔记。  

###一.什么是nodejs？  
实际上是采用google的chrome浏览器V8引擎，由C++编写的。  
本质上是一个javascript的运行环境
浏览器引擎可以解析js代码
nodejs可以解析js代码，没有浏览器端各种安全性的限制，还提供许多系统级别的API：
  
1、文件的读写
2、进行的管理
3、网络通信

###二.为什么学习node.js？(表示基本都看不懂老师说的是什么。。。O-O)
  
  
Node-Webkit,appjs :允许用户使用html/css/javascript开发跨平台桌面应用程序，并且兼容Linux，Windows
  
Jade：和Nodejs组合使用，方便高校管理后台html模板
  
Gost:开元博客程序
  
Grunt：Javascript跑各种任务的工具，完成样式工具，语法检查，自动化测试等任务
  
gulp: 和grunt功能相似，不过配置比较简单
  
Express.js:
  
Nodecast:
  
Log.io：实时监控项目日志
  
PDFKit：生成文档
  
Haroopad：Linux上的MarkDown在编辑器
  
NoduinoWeb：控制开源硬件
  
NodeOS：操作系统

  
学习的相关网站
  
1、nodejs.org 看nodejs的版本升级，新特性的加入，重要bug的修复等，api变化，功能变化-未来发展趋势。
  
2、www.npmjs.com 模块社区，看他人源代码，学习理念
  
3、github.com 开源项目和源码
  
4、stackoverflow.com 技术解答社区，查询相关资源，环境配置，异常解决方法等
###三.如何安装node.js
[如何安装node.js](http://www.imooc.com/video/6691)  
###四。node.js写helloworld
[起一个web服务器](http://nodejs.cn/doc/node/synopsis.html)  

  
1.设置自己的文件夹，在文件夹beginning里新增server.js
  
2.server.js内容：
  
 var http = require('http');
  
 http.createServer(function(req,res){
  
 res.writeHead(200,{'Content-type':'text/plain'});
  
 res.end('Hello World\n');}).listen(1337,'127.0.0.1');
  
 console.log('Server running at http://127.0.0.1:1337/');
}
  
3.首先要通过cd 命令 进入beginning[本地] 文件夹 cd imooc/    
  
beginning
  
 命令行：node server.js 启动
  
（1337端口是本身代码里设置的）
  
4.先在 cmd中 启用或者重启 服务器 （node server.js)，再在浏览器     
中刷新页面
  
5.http对象可以创建一个server对象，并把这个创建的对象赋值给server。
   
var http=require('http');
  
 var server=http.createServer(function(req,res){
  
 res.writeHead(200,{'Content-Type':'text/plain'});
  
 res.end('Hello Node.js ,This is a Node.js http server   demo\n');
  });
  
 server.listen(1337,'127.0.0.1');
  
 console.log('Server running at http://127.0.0.1:1337/');
  
6.ctrl+c停止服务器，修改请求或是响应代码，要重启服务器
###四.node.js和浏览器环境的一同
node.js和浏览器执行环境  
 
相同点：都能执行一般的Js代码
  
不同点：全局变量不同，例如window，document等只能在浏览器中取到，而process则只能在node环境中取到。
  
宿主：浏览器，node；
  
全局变量：浏览器-window、document;node - process。  
nodejs本质是一个js的执行环境。由于封装和底层的处理赋予了更大的能力
#summary：
##一头雾水，全是概念。