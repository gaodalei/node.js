#day3
##慕课网学习node.js笔记
###一.URL对象  
[官方文档  url](http://nodejs.cn/doc/node/url.html#url)  
URL：统一资源定位符。  
URI：统一资源标示符 。  
1.url.parse(url,boolean1,boolean2)  
url地址  
boolean1：最后解析出来的query部分，是否以对象形式返回，default to false。  
boolean2：Pass true as the third argument to treat //foo/bar as { host: 'foo', pathname: '/bar' } rather than { pathname: '//foo/bar' }. Defaults to false.  
2.url.resolve(from, to)
Take a base URL, and a href URL, and resolve them as a browser would for an anchor tag. Examples:
url.resolve('/one/two/three', 'four')         // '/one/two/four'
url.resolve('http://example.com/', '/one')    // 'http://example.com/one'
url.resolve('http://example.com/one', '/two') // 'http://example.com/two'  
3.url.format(urlObj): 将对象解析成定位符

###二.querystring.stringfy()与querystring.parse()   
 
1.querystring.stringify(obj,sign1,sign2)//将对象转化成url中query部分的形式  
 参数：  
(1).要转化的对象   
(2).链接符（默认&）  
(3).键与值之间的符号（默认=）querystring.parse(string,sign1,sign2,sign3)//将query字符串转化成对象（反序列华）  
 
参数：  
1.query字符串  
2.链接符（默认&）  
3.
键与值之间的符号（默认=）  
4.参数的个数（默认最多1000个，0就没有限制）  

querystring.escape(string) //文字转译  

querystring.unescape(string) //反转译
###三.作用域和上下文。
this内部对象，只能在内部使用，指向函数拥有者，拥有者叫做上下文，根据运行环境而定。  

（1）在全局环境运行的上下文，this指向全局对象。浏览器中的window对象，nodejs里面的global。  
  
在函数内部的this取决于函数调用方式。如下三种方式：  

<pre><code>（2）  作为对象的方法
var pet={
	word:"hello"，
	speak:function(){
		console.log(this.word);
		console.log(this==pet);//true
}
pet.speak();
（3）function pet(word){
	this.word=word;
	console.log(this.word);
	console.log(this===global);//true
}
pet("hello");//nothig
(4)function pet(word){
	this.word=word;
	this.speak=function(){
		console.log(this.word);	
		console.log(this===person);//true
}
}
var person=new pet("hello");
person.speak();
</code></pre>
##之所以说这些，是为了引出call和apply方法
明天再说

