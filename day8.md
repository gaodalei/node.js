#day7
##慕课网学习node.js笔记
###mongodb模式设计以及编码
#太多不懂，mongodb，一脸蒙蔽！只知道怎么做，不知道为啥！
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