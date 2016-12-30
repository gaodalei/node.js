###day7
##慕课网学习node.js笔记
###项目结构
如图：
![](/img/2.png)

步骤：  
###1，写出四个页面的视图文件，使用jade。4个页面的样式，继承了layout.jade。  
（1）layout.jade
<pre><code>
doctype
  html
	head
	  meta(charset="utf-8")
		title #(title)
	  include ./includes/head
	body
	  include ./includes/header
	  block content//内容区块
	</pre>
（2）head和header  
header.jade如下：
<pre><code>.container
  .row
    .page-header
	  h1=title  
</code></pre>
head.jade如下：把引入的css和js写在这里
<pre><code>script（src=""）
link(href="" rel="stylesheet")
</pre>
（3）index.jade首页  
![](/img/3.png)  
<pre><code>
html代码如下：

....
先写出html的代码，再翻译成jade
</pre>
翻译出来的jade如下：
<pre><code>extend ../layout
extend ../layout
block content
	.container
		.row
			each item in movies
				.col-md-2
					.thumbnail
						a(href="/detail/#{item._id}")
							img(src="#{item.poster}",alt="#{item.title}")
						.caption
							h3 #{item.title}
							p: a.btn.btn-primary(href="/detail/#{item._id}",role="button")观看预告片
</pre>
###二.app.js
<pre><code>var express=require('express');//加载express模块
var port=process.env.PORT||3000;//设置端口号：3000
var app = express();//实例化一个express
app.use(express.static(__dirname+'./bower-components'));//设置express使用css和js位置。
app.set('views','./views/pages');//设置视图文件位置，即jade所在位置
app.set（'view engine','jade'）;//设置模板引擎，jade。
app.listen(port);//监听这个端口

console.log("obj started on port:"+port);//在控制台输出服务器开启成功

//路由

//1.index page
app.get('/',function(req,res){
	res.render('index',{title:imooc首页，movies：[
{title：'机械战警'，poster:'........',_id:'1'},
{title：'机械战警1'，poster:'........',_id:'2'},
{title：'机械警察2'，poster:'........',_id:'3'},
{title：'机械战警3'，poster:'........',_id:'4'},
{title：'机械战警4'，poster:'........',_id:'5'},
{title：'机械战警5'，poster:'........',_id:'6'}
]
})
})