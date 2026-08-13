### HTML(HyperText Markup Language):超文本标记语言。
超文本:超越了文本的限制,比普通文本更强大。除了文字信息,还可以定义图片、音频、视频等内容。
标记语言:由标签“<标签名>”构成的语言
```
HTML标签都是预定义好的。例如:使用<h1>展示标题,使用<img>展示图片,使用<video>展示视频。
HTML代码直接在浏览器中运行,HTML标签由浏览器解析。
```
### CSS(Cascading Style Sheet):层叠样式表,用于控制页面的样式(表现)
MDN有关于这些的说明文档
[MDN Web Docs](https://developer.mozilla.org/zh-CN/)
HTML基本骨架标签
```
<html>
<head>
</head>
<body>
<title>HTML快速入门</title>
<h1>Hello HTML</h1>
<img src="img/1.png">
</body>
</html>
```
HTML标签特点
```
html标签不区分大小写,建议小写
html标签的属性值使用单引号/双引号都可以
html语法结构松散,但是建议规范书写
```

### VsCode开发工具
一些实用插件：
```
Chinese (Simplified) Langu ...
HTML CSS Support
JavaScript (ES6) code snip ...
Mithril Emmet
Path Intellisense
Vue 3 Snippets
Auto Close Tag
Auto Rename Tag
open in browser
Live Server
Vue - Official
File Utils
IntelliJ IDEA Keybindings//可以让vscode的快捷键和idea的一样
TRAE AI: Coding Assistant
Qoder CN
```
快捷结构标签：输入英文的！+enter 直接生成HTML的主体结构
注释的快捷键：ctrl+/
```
<!-- 声明文档的类型为html -->
<!DOCTYPE html>
<html lang="en">
<head>
<!-- 字符集 -->
    <meta charset="UTF-8">
    <!-- 设置网页在移动设备上的显示宽度及缩放比例 -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- 网页导航标题 -->
    <title>Document</title>
</head>
<body>

</body>
</html>
```
 可以借助ai来写代码
 鼠标悬停在标签上方可以去MDN查看这个标签的信息，特别好用
 右键文件有创建副本的选项
```
 <!-- 定义一个央视网的超链接标签 -->
     <a href="https://www.cctv.com">央视网</a>
```
```
<!-- 定义一段文本内容,内容为:2026年6月13日颜色浅灰 -->
<span style="color: #888;">2026年6月13日</span>//没有语义的标签
```
CSS引入方式:
```
行内样式:写在标签的style属性中(配合JavaScript使用)
内部样式:写在style标签中(可以写在页面任何位置,但通常约定写在head标签中)
外部样式:写在一个单独的.css文件中(需要通过 link 标签在网页中引入)
```
![[Pasted image 20260809202027.png]]
想知道具体的颜色信息可以使用拾色器，比如snipaste这个软件既可以截图也可以获取颜色
![[Pasted image 20260809202721.png]]
![[Pasted image 20260809202925.png]]
优先级：id>类>元素
![[Pasted image 20260809211714.png]]
```
 <!-- 定义一个视频，引入视频文件 -->
     <video src="video/1.mp4" controls></video>
```
属性详情可以去MDN去查看
px是像素，屏幕的最小单位
宽度和高度只设置一个即可，因为会等比例缩放
%百分比，相对于父元素的百分比
换行标签br
```
     <!-- 定义一个音频，引入音频文件 -->
     <audio src="audio/1.mp3" controls></audio>
```
段落标签p，段落和段落之间会有间隙
strong,b标签表示加粗
p标签的行高通过css样式来更改
```
     <p>
      这是一个段落
     </p>
     <p>
      这是第二个段落
     </p>
```
相对路径
./ 表示当前目录
../表示上一级目录
```
     &nbsp;
     <!-- 这是&nbsp;一个&nbsp;段落，表示一个空格 -->
```
```
     小于号&gt;
     大于号&lt;
```
### 盒子模型(css)
盒子:页面中所有的元素(标签),都可以看做是一个 盒子,由盒子将页面中的元素包含在一个矩形区域内,通过盒子的视角更方便的进行页面布局
盒子模型组成:内容区域(content)、内边距区域(padding)、边框区域(border)、外边距区域(margin)
![[Pasted image 20260810093111.png]]
```
<div> 标签:
一行只显示一个(独占一行)
宽度默认是父元素的宽度,高度默认由内容撑开
可以设置宽高(width、height)
宽高默认是内容区的
可以通过css样式来设置指定哪个区
padding: 20px 20px 20px 20px;
border: 20px solid #6bd5d7;
margin: 30px 30px 30px 30px;
这四个值分别表示顺时针方向的边距，上右下左
如果只有两个，第一个表示上下，第二个表示左右，第二个设置为auto表示左右居中
只有一个就是全部都是
```
```
<span>标签:
一行可以显示多个
宽度和高度默认由内容撑开
可以设置宽高(width、height)
```
### flex布局(css)
flex是flexible Box的缩写,意为“弹性布局”,是一种一维的布局模型。flex布局可以为元素之间提供强大的空间分布和对齐能力。
通过给父容器添加flex的相关属性,来控制子元素的位置和排列方式。
![[Pasted image 20260810101705.png]]
### 表单标签
```
表单:在网页中主要负责数据采集功能,如 注册、登录等数据采集。
标签 :<form>
表单项:不同类型的 input 元素、下拉列表、文本域等。
<input>:定义表单项,通过type属性控制输入形式(text/password/ ... )
<select>:定义下拉列表,<option>定义列表项。
<textarea>:定义文本域
```
action:表单数据提交的ur1地址
method:提交方式
get:默认,表单数据会出现在ur1后面,形式:/save?name=Tom&age=18
特点:
如果表单中包含了隐私数据,get方式并不安全,不推荐使用该方式.
在浏览中get请求的大小是有限制的,不适合提交大数据量的表单。
post:表单数据会在消息体/请求体中提交到服务器
特点:
安全
请求大小没有限制
#### 注意:表单项要想能够采集数据,必须得设置name属性,表示当前表单项的名字
比如
```
<input type="text" id="name" name="name" placeholder="请输入员工姓名">
<select id="gender" name="gender">
<select id="position" name="position">
```
这些才能被表单采集数据
如何查看这个消息体以及消息体里面的数据：按F12进入开发者工具，选择网络->全部->选择对应的请求->标头->负载，这里可以看到里面的数据
### 表单项
```
<input>:定义表单项,通过type属性控制输入形式(text/password/ ... )
<select>:定义下拉列表,<option>定义列表项。
<textarea>:定义文本域
```
![[Pasted image 20260810110042.png]]
单选按钮如果是一组的必须name属性一样
label标签包裹的可以扩大鼠标的选中范围
### 表格table
thead表头
tbody表格的主体
tr表格的行
td表格的列
![[Pasted image 20260810134451.png]]
