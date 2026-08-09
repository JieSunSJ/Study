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