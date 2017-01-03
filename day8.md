#day8
##慕课网学习node.js笔记
###mongodb模式设计以及编码

![](/img/mogodb.png)  
####1，schema模式定义：  
<pre>var mongoose=require('mongoose');
var MovieSchema =new mongoose.schema({
	director:String,
	title:String,
	country:String,
	year:Number,
	summary:String
});</pre>
####2,model编译模型  
<pre>var mongoose=require('mongoose');
var movieSchema=require('../schemas/movie');
var movie=mongoose.model('movie',movieSchema);
module.exports=movie;</pre>
####3.documents实例化
![](./img/schema3.png)
####4.schema中documents的查询
#####（1）批量
![](./img/schema2.png)
#####(2)单条
![](./img/schema1.png)


#summary:
#太多不懂，mongodb，一脸蒙蔽！只知道怎么做，不知道为啥！这个地方跟老师的使用有差别，明天尽量搞懂这个demo。

