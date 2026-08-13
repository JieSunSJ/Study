## 入门
介绍:Asynchronous JavaScript And XML,异步的JavaScript和XML。
XML:(英语:Extensible Markup Language)可扩展标记语言,本质是一种数据格式,可以用来存储复杂的数据结构。
作用:
数据交换:通过Ajax可以给服务器发送请求,并获取服务器响应的数据。
异步交互:可以在不重新加载整个页面的情况下,与服务器交换数据并更新部分网页的技术,如:搜索联想、用户名是否可用的校验等等。
## Axios
介绍:Axios 对原生的Ajax进行了封装,简化书写,快速开发。
官网:https://www.axios-http.cn/
步骤:
·引入Axios的js文件(参照官网)
·使用Axios发送请求,并获取响应结果
```
<body>
    <input type="button" value="获取数据GET" id="btnGet">
    <input type="button" value="发送数据POST" id="btnPost">
    <script>
        document.querySelector("#btnGet").addEventListener("click",()=>{
            //axios发起异步请求
            axios({
                url:"https://api.github.com/users/mzj-x",
                method:"get"
            }).then(res=>{//成功回调函数
                console.log(res.data)
            }).catch(err=>{//失败回调函数
                console.log(err)
            })
        })
        document.querySelector("#btnPsot").addEventListener("click",()=>{
            //axios发起异步请求
            axios({
                url:"https://api.github.com/users/mzj-x",
                method:"post",
                data:'id=1'
            }).then(res=>{//成功回调函数
                console.log(res.data)
            }).catch(err=>{//失败回调函数
                console.log(err)
            })
        })
    </script>
```
Axios-请求方式别名
为了方便起见,Axios已经为所有支持的请求方法提供了别名
格式:axios.请求方式(url [,data [,config]])
```
axios.get('https://mock.apifox.cn/m1/3083103-0-default/emps/list').then((result) => {
console.log(result.data);
}).catch((err) => {
console.log(err);
});
```
```
axios.post('https://mock.apifox.cn/m1/3083103-0-default/emps/update','id=1').then((result) => {
console.log(result.data);
}).catch((err) => {
console.log(err);
});
```
```
https://web-server.itheima.net/emps/list
```
## 案例
在网址后面的?name=&gender=1&job=3其实就是查询条件
## async & await
可以通过async、await可以让异步变为同步操作。async就是来声明一个异步方法,await是用来等待异步任务执行。
```
methods: {
async search(){
//根据用户输入的搜索条件,基于axios发送异步请求(https://web-server.itheima.net/emps/list)到服务端 ...
let result =  await axios.get('https://web-server.itheima.net/emps/list?name=xxx&gender=xxx&job=xxx');
this.employees = result.data.data;
}
```
## Vue生命周期
生命周期:指一个对象从创建到销毁的整个过程。
生命周期的八个阶段:每触发一个生命周期事件,会自动执行一个生命周期方法(钩子)。
![[Pasted image 20260812083333.png]]
```
<script type="module">
import { createApp } from 'https:// ... /vue.esm-browser.js'
const app = createApp({
data() {
return {
message: "Hello Vue"

}

},
//生命周期-钩子函数 mounted
mounted() {
console!log('Vue挂载完毕,发送请求获取数据

}).mount("#app") ;
</script>
```
### Vue生命周期典型的应用场景?
· 在页面加载完毕时,发起异步请求,加载数据,渲染页面。