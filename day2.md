#day2
##慕课网学习node.js笔记
###一.common.js与模块
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;JS中容易出现变量被覆盖，方法被替代的情况（既被污染）。特别是存在依赖关系时，容易出现错误。这是因为JS缺少模块管理机制，来隔离实现各种不同功能的JS片段，避免它们相互污染。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Commonjs是一套规范，约定了js如何组织，如何编写。大部分标准在拟定和讨论之中，首先把执行不同任务的代码块和代码文件看为独立的模块，每一个模块都是一个单独的作用域，但不是孤立的，可能存在依赖关系。每个模块分为三个部分，定义、标识和引用。nodejs和common.js实现了模块管理系统。node中每一个js文件都是一个独立的模块，在其内部不需要有命名空间。
###二.模块的分类  
在nodejs中文件和模块是一一对应的  
模块类型： 1核心模块  2本地模块 3通过npm安装的第三方模块  
引用模块的方式：  1用文件路径引用  2用模块名来引用  
如果用名称引用非核心模块的话，node就会把模块名映射到对应模块名的路径 ，包含了核心函数的模块会在node启动时预先加载 。非核心模块就是使用npm安装的第三方模块，或者其他人创建的模块。  
核心模块：http ，fs， path  
文件模块：var util = require('./util.js'); 文件名   
第三方模块：var promise = require('bluebird')  模块名   
###三.实现一个简单的模块。  
步骤：  
 
<pre><code>
1：创建模块 
./student.js  
function add(student){
  console.log("addStudent:"+student);
}
2.导出模块
export add=add;

./teacher.js
function add(teacher){
	console.log("addTeacher:"+teacher);
}
export add=add;
./klass.js
3.加载模块
var student=require("./student.js");
var teacher=require("./teacher.js");
function add(teacherName,students){
4.使用模块
	teacher.add(teacherName)；
	students.forEach(function(item,index){
	student.add(item);
})
}
exports.add=add;

./shool.js
var klass=require("./klass.js");
4.使用模块
klass.add("老师a"，["小明"，"小红"，"小强"])；

</pre>
![](./img/1.png)
*exports.add = add;和 module.exports = add 不同点。注意
：exports.add是传统的模块实例，module.exports是特别的对象类型，支持存在的东西。
#summary：    
##有点小懂。






