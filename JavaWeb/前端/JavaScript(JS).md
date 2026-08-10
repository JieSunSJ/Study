负责网页的行为(交互效果)
JavaScript(简称:JS)是一门跨平台、面向对象的脚本语言,是用来控制网页行为,实现页面的交互效果。
JavaScript 和 Java 是完全不同的语言,不论是概念还是设计。但是基础语法类似。
组成:
ECMAScript:规定了JS基础语法核心知识,包括变量、数据类型、流程控制、函数、对象等。
BOM:浏览器对象模型,用于操作浏览器本身,如:页面弹窗、地址栏操作、关闭窗口等。
DOM:文档对象模型,用于操作HTML文档,如:改变标签内的内容、改变标签内字体样式等。
## JS核心语法
### Js引入方式
```
内部脚本:将JS代码定义在HTML页面中
JavaScript代码必须位于 <script></script>标签之间
在HTML文档中,可以在任意地方,放置任意数量的<script>
一般会把脚本置于<body>元素的底部,可改善显示速度
外部脚本:将 JS代码定义在外部 JS文件中,然后引入到HTML页面中
```
```
<body>
    <!-- <script>
        // 1.内部脚本
        alert('Hello JS')
    </script> -->
    <!-- 外部脚本 -->
    <script src="./js/dome.js"></script>
</body>
```
JS书写规范
结束符:每行结尾以分号结尾,结尾分号可有可无,要么全部加上，要么全不加
### 基础语法
#### 变量
```
JS中用 let 关键字来声明变量(弱类型语言,变量可以存放不同类型的值)。
变量名需要遵循如下规则:
只能用 字母、数字、下划线(_)、美元符号($)组成,且数字不能开头
变量名严格区分大小写,如 name 和 Name 是不同的变量
不能使用关键字,如:let、var、if、for等
JS中用 const 关键字来声明常量。
一旦声明,常量的值就不能改变(不可以重新赋值)
注意:
· 在早期的js中,声明变量还可以使用var,但是并不严谨(不推荐)
```

```
<body>
    <script>
        let a = 10
        a = "Hello JS"
        alert(a)//弹出框(使用频率较高)
        const b = 20
        //b = "Hello JS"
        console.log(b)//输出到控制台(使用频率较高)
        document.write(a)//直接输出到body区域，不常用
    </script>
</body>
```
### 数据类型
JavaScript的数据类型分为:基本数据类型和引用数据类型(对象)。
基本数据类型:
number:数字(整数、小数、NaN(Not a Number,不是一个数的数))
boolean:布尔。true,false
null:对象为空。JavaScript是大小写敏感的,因此null、Null、NULL是完全不同的
undefined:当声明的变量未初始化时,该变量的默认值是 undefined
string:字符串,单引号、双引号、反引号皆可,推荐使用单引号
使用 typeof 运算符可以获取数据类型:
```
  <body>
    <script>
      //1. 数据类型
      alert(typeof 10); //number
      alert(typeof 1.5); //number
      alert(typeof true); //boolean
      alert(typeof false); //boolean
      alert(typeof "Hello"); //string
      alert(typeof "JS"); //string
      alert(typeof "JavaScript"); //string
      alert(typeof null); //object
      let a;
      alert(typeof a); //undefined
    </script>
  </body>
```
```
模板字符串语法:
·``(反引号,英文输入模式下按键盘的tab键上方波浪线~那个键)
· 内容拼接变量时,使用 $[} 包住变量
```
```
    //2.模板字符串 -简化字符串拼接
    let name = "JS";
    let age = 18;
    let info = `我的名字是${name}，年龄是${age}`;
    console.log(info);
```
### 函数
介绍:函数(function)是被设计用来执行特定任务的代码块,方便程序的封装复用。
定义:JavaScript中的函数通过function关键字进行定义,语法为:
```
function add(a, b){
return a + b;
}
```
调用：函数名称(实际参数列表)
```
//具名函数
    <script>
        function add(a,b){
           return a+b
        }
        let result = add(10,20)//传入3个第三个会被忽略
        console.log(result)
    </script>
```
```
        //匿名函数
        //函数表达式
        let add = function(a,b){
            return a+b
        }
        //箭头函数
        let add = (a,b) => {
            return a+b
        }
        let result2 = add(10,20)
        console.log(result)
```
### 自定义对象
格式：
```
let 对象名={
属性名1:属性值1,
属性名2:属性值2,
属性名3:属性值3,
//注意:在箭头函数中,this并不指向当前对象 - 指向的是当前对象的父级
方法名:function(形参列表){}//:function可以省略
}
//省略过后
方法名(){
}
```
调用方式：
对象名.属性名
对象名.方法名
```
    <script>
        let a = {
            name:"JS",
            age:18,
            show(){
                console.log(`${this.name}---${this.age}`)
            }
        }
        a.show()
        console.log(a.name)
    </script>
```
### JSON
概念:JavaScript Object Notation,JavaScript对象标记法(JS对象标记法书写的文本)
由于其语法简单,层次结构鲜明,现多用于作为数据载体,在网络中进行数据传输。
JSON格式特点:json格式的文本所有的key必须使用双引号引起来
前后端交互传递的是JSON格式
JSON提供的两个方法
JSON.parse( .. )//将JSON转换成js对象

JSON.stringify( .. )//将js对象转化为JSON
```
    <script>
        let a = {
            name:"JS",
            age:18,
            sex:"男"
        }
        alert(JSON.stringify(a))//js对象-->json字符串
        let aJson = '{"name":"JS","age":18,"sex":"男"}'
        alert(JSON.parse(aJson).name)//json字符串-->js对象
    </script>
```
### DOM
DOM文档在[JavaScript 和 HTML DOM 参考手册](https://www.w3school.com.cn/jsref/index.asp)
详细请查看HTML对象
概念:Document Object Model,文档对象模型。
将标记语言的各个组成部分封装为对应的对象:
Document:整个文档对象
Element:元素对象
Attribute:属性对象
Text:文本对象
Comment:注释对象
JavaScript 通过DOM,就能够对HTML进行操作:
改变 HTML 元素的内容
改变 HTML 元素的样式(CSS)
对 HTML DOM 事件作出反应
添加和删除 HTML 元素
![[Pasted image 20260810163433.png]]
DOM操作
DOM操作核心思想:将网页中所有的元素当做对象来处理。(标签的所有属性在该对象上都可以找到)
操作步骤:
获取要操作的DOM元素对象
操作DOM对象的属性或方法(查文档或AI)
获取DOM对象
根据CSS选择器来获取DOM元素,获取匹配到的第一个元素:document.querySelector('选择器')
根据CSS选择器来获取DOM元素,获取匹配到的所有元素:document.querySelectorAll('选择器')
注意:得到的是一个NodeList节点集合,是一个伪数组(有长度、有索引的数组)
```
<body>
    <h1 id="id1">1111</h1>
    <h1>2222</h1>
    <h1>3333</h1>
    <script>
        //修改第一个h1标签的文本内容
        //1.1获取DOM对象
        let h1 = document.querySelector("#id1");//参数填选择器
        //1.2调用DOM对象中属性或方法
        h1.innerHTML = "4444"
        let h2 = document.querySelectorAll("h1");
        h2[1].innerHTML = "5555";
    </script>
</body>
```
### 事件监听
什么是事件?什么是事件监听?
事件:HTML事件是发生在HTML元素上的“事情”。比如:
按钮被点击
鼠标移动到元素上
按下键盘按键
事件监听:JavaScript可以在事件触发时,就立即调用一个函数做出响应,也称为 事件绑定或注册事件。

语法:
```
事件源.addEventListener('事件类型',事件触发执行的函数);
```
事件监听三要素
```
事件源:哪个dom元素触发了事件,要获取dom元素
事件类型:用什么方式触发,比如:鼠标单击 click
事件触发执行的函数:要做什么事
```
```
<body>
    <button id="btn">点击</button>
    <script>
        //事件监听 -addEventListener (可以多次绑定同一事件)
        document.querySelector("#btn").addEventListener("click",()=>{
            alert("点击了按钮")
        })
        document.querySelector("#btn").addEventListener("click",()=>{
            alert("点击了按钮")
        })
        //事件绑定的早期写方法(如果多次绑定同一个事件，会覆盖)
        document.querySelector("#btn").onclick = function(){
        console.log("点击了按钮")
        }
    </script>
</body>
```


