#day4
##慕课网学习node.js笔记
###一。非阻塞，单线程，事件驱动：

1. 什么是回调？
回调是异步编程时的基础，将后续(注意理解这个后续。。。)逻辑封装成起始函数的参数，逐层嵌套  
栗子：<pre><code>
function readFileCallBack(err, data) {
if (err) {
console.error(err);
} else {
console.log(data);
}
}
var fs = require('fs');
fs.readFile('file.txt', 'utf-8', readFileCallBack);
console.log('end.');</code></pre>
2. 什么是同步/异步？
同步是指：发送方发出数据后，等接收方发回响应以后才发下一个数据包的通讯方式。  
异步是指：发送方发出数据后，不等接收方发回响应，接着发送下个数据包的通讯方式。  
3. 什么是I/O？
磁盘的写入（in）磁盘的读取（out）
4. 什么的单线程/多线程？
一次只能执行一个程序叫做单线程
一次能执行多个程序叫多线程
5. 什么是阻塞/非阻塞？
阻塞：前一个程序未执行完就得一直等待
非阻塞：前一个程序未执行完时可以挂起，继续执行其他程序，等到使用时再执行
6. 什么是事件？
一个触发动作（例如点击按钮）
7. 什么是事件驱动？
<PRE><CODE>
var eventEmitter=require('events').EventEmitter;
var event =new eventEmitter();
event.on('some_event',function(){
	console.log("some event ocurred!");
})
setTimeout(function(){
	event.emit('some_event');
},1000)
图片</code>

一个触发动作引起的操作（例如点击按钮后弹出一个对话框）
8. 什么是基于事件驱动的回调？
为了某个事件注册了回调函数，但是这个回调函数不是马上执行，只有当事件发生的时候，才会调用回调函数，这种函数执行的方式叫做事件驱动~这种注册回调就是基于事件驱动的回调，如果这些回调和异步I/O(数据写入、读取)操作有关，可以看作是基于回调的异步I/O，只不过这种回调在nodejs中是有事件来驱动的

9. 什么是事件循环？
//事件循环Eventloop,倘若有大量的异步操作，一些I/O的耗时操作，甚至是一些定时器控制的延时操作，它们完成的时候都要调用相应的回调函数，从而来完成一些密集的任务，而又不会阻塞整个程序执行的流程，此时需要一种机制来管理，这种机制叫做事件循环.
总而言之就是：管理大量异步操作的机制叫做事件循环

Event Loop:
回调函数队列。异步执行的函数会被压入这个队列; 队列被循环查询。  
###二.性能测试
cd到apache的bin目录下，然后cmd控制台：ab -n1000 -c10 http://www.baidu.com/  
-n：总共的请求数，-c并发数。缺省值都为1。  
###三.node.js的repl（交互式解释器）

###四，node.js读取文件。
####异步请求，回调函数  
<pre><code>
异步读取格式如下：
fs.readFile(filename, [encoding], [callback(err,data)])。
栗子：
var rf=require("fs");
var data=rf.readFile("test","utf-8"，function(error，data)
	if(error){
		console.log("error");
	}else{
		console.log(data);
	}
);
console.log(data);
console.log("READ FILE SYNC END");	
解释：rf.readfile调用时，将异步i/o请求发送给了系统，然后立即返回bing执行后面的语句，执行完成以后，进入事件循环监听事件，当rf接收到i/o请求完成的事件后，时间循环会主动调用回调函数已完成以后的工作。
</code></pre>
  
