Vue是一款用于构建用户界面的渐进式的JavaScript框架。
框架:就是一套完整的项目解决方案,用于快速构建项目。
优点:大大提升前端项目的开发效率。
缺点:需要理解记忆框架的使用规则。(参照官网)
[Vue.js - 渐进式 JavaScript 框架 | Vue.js](https://cn.vuejs.org/)
Vue核心包开发-局部 模块改造
Vue 核心包-Vue插件工程化开发-整站开发
## Vue快速入门
准备
· 引入Vue模块(官方提供)
· 创建Vue程序的应用实例,控制视图的元素
· 准备元素(div),被Vue控制
数据驱动视图
· 准备数据
· 通过插值表达式渲染页面
官网的ES模块构建版本
```
<div id="app">{{ message }}</div>//插值表达式一定要在div盒子里面

<script type="module">
  import { createApp, ref } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js'
  
  createApp({
    setup() {//这里选正方形setup可以直接生成下面的模块
      const message = ref('Hello Vue!')
      return {
        message
      }
    }
  }).mount('#app')
</script>
```
## Vue常用指令
指令:HTML标签上带有 v-前缀的特殊属性,不同的指令具有不同的含义,可以实现不同的功能。
常用指令：
![[Pasted image 20260811132210.png]]
### v-for
作用:列表渲染,遍历容器的元素或者对象的属性值
快捷键vfor
语法:
```
<tr v-for="(item, index) in items" :key="item.id"> {{item}}</tr>
```
参数说明:
· items 为遍历的数组
· item 为遍历出来的元素
· index 为索引/下标,从0开始;可以省略,省略index语法:v-for="item in items
key:
· 作用:给元素添加的唯一标识,便于vue进行列表项的正确排序复用,提升渲染性能
· 推荐使用id作为key(唯一),不推荐使用index作为key(会变化,不对应)
```
    <script type="module">
        import { createApp } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js'
        const app = createApp({
            data() {
                return {
                    items: [
                        {
                            id: 1,
                            name: '令狐冲',
                            gender: '男',
                            avatar: 'img/屏幕截图 2026-03-13 223519.png',
                            position: '讲师',
                            entryDate: '2020-03-15',
                            lastOperationTime: '2026-08-10 09:30:00'
                        },
                        {
                            id: 2,
                            name: '令狐冲',
                            gender: '男',
                            avatar: 'img/屏幕截图 2026-03-13 223519.png',
                            position: '讲师',
                            entryDate: '2020-03-15',
                            lastOperationTime: '2026-08-10 09:30:00'
                        }
                    ]
                }
            }
        }).mount('#app')
    </script>
```
```
<div id="app">
            <tbody>
                <tr v-for="(item, index) in items" :key="item.id">
                    <td>{{ item.name }}</td>
                    <td>{{ item.gender }}</td>
                    <td><img :src="item.avatar" id="img1"></td>
                    <td><span class="tag tag-lecturer">{{ item.position }}</span></td>
                    <td>{{ item.entryDate }}</td>
                    <td>{{ item.lastOperationTime }}</td>
                    <td>
                        <a href="#" class="btn-edit">编辑</a>
                        <a href="#" class="btn-delete">删除</a>
                    </td>
                </tr>
            </tbody>
</div>
```
插值表达式不能出现在标签内部
### v-bind
作用:动态为HTML标签绑定属性值,如设置href,src,style样式等。
语法:v-bind:属性名="属性值”
```
<img v-bind:src="item. image" width="30px">
```
简化 :: 属性名="属性值"
```
<img :src="item. image" width="30px">
```
### v-if & v-show
· 作用:这两类指令,都是用来控制元素的显示与隐藏的
. v-if
· 语法:v-if="表达式”,表达式值为 true,显示;false,隐藏
原理:基于条件判断,来控制创建或移除元素节点(条件渲染)
场景:要么显示,要么不显示,不频繁切换的场景
其它:可以配合 v-else-if /v-else 进行链式调用条件判断
```
<span class="tag tag-lecturer" v-if="item.position == 1">讲师</span>
<span class="tag tag-teacher" v-else-if="item.position == 2">老师</span>
```
![[Pasted image 20260811142944.png]]
只渲染条件符合的，条件不符合就不渲染
### v-show
· 语法:v-show="表达式”,表达式值为 true,显示;false,隐藏
原理:基于CSS样式display来控制显示与隐藏
场景:频繁切换显示隐藏的场景
```
<span v-show="item.position == 1">老师</span>
<span v-show="item.position == 2">讲师</span>
```
![[Pasted image 20260811142753.png]]
v-show都会被渲染，只不过通过css样式被隐藏了
### v-model
作用:在表单元素上使用,双向数据绑定。可以方便的 获取 或 设置 表单项数据
语法:v-model="变量名"
v-model 中绑定的变量,必须在data中定义。
```
                    search: {
                        name: '',
                        gender: '',
                        position: ''
                    }
```
```
<input type="text" id="name" name="name" v-model="search.name" placeholder="请输入员工姓名">


<select id="gender" name="gender" v-model="search.gender">
                    <option value="">请选择</option>
                    <option value="男">男</option>
                    <option value="女">女</option>
                </select>
                
<select id="position" name="position" v-model="search.position">
                    <option value="">请选择</option>
                    <option value="前端工程师">前端工程师</option>
                    <option value="后端工程师">后端工程师</option>
                </select>
```
可以直接在页面用插值表达式来获取这个值验证有没有被绑定

下载Vue.js Devtools插件就可以通过F12来查看Vue的数据模型了
![[Pasted image 20260811154858.png]]
### v-on
· 作用:为html标签绑定事件(添加事件监听)
· 语法:
· v-on:事件名="方法名”
· 简写为@事件名=" …. "
```
<div id="app">
<button type="button" v-on:click="handle"></button>
<button type="button" @click="handle"></button>
</div>
```
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <!--
        ============================================
        1. 整个页面用 <div id="app"> 包裹，作为 Vue 的挂载点
           注意：不能把 <table> 作为挂载点，因为浏览器会把
           <form>、<button> 等非表格元素弹出到 <table> 外面，
           导致 Vue 无法正确渲染。
        ============================================
    -->
    <div id="app">
        <!--
            ============================================
            2. 搜索表单
               @submit.prevent="getData"
               - @submit：监听表单的提交事件
               - .prevent：阻止表单的默认提交行为（页面不会刷新跳转）
               - ="getData"：触发 getData 方法，发送请求

               v-model：双向绑定，输入框/下拉框的值变化时，
               searchForm 对象里的对应属性也会同步更新。
            ============================================
        -->
        <form @submit.prevent="getData">
            <!-- 输入姓名，v-model 绑定到 searchForm.name -->
            <input type="text" v-model="searchForm.name" placeholder="姓名">

            <!-- 选择性别，v-model 绑定到 searchForm.gender -->
            <select v-model="searchForm.gender">
                <option value="">请选择性别</option>
                <option value="1">男</option>
                <option value="2">女</option>
            </select>

            <!-- 选择职位，v-model 绑定到 searchForm.job -->
            <select v-model="searchForm.job">
                <option value="">请选择职位</option>
                <option value="1">前端工程师</option>
                <option value="2">后端工程师</option>
            </select>

            <!--
                type="submit"：点击这个按钮会触发表单的 submit 事件
                然后执行 @submit.prevent="getData"
            -->
            <button type="submit">查询</button>

            <!--
                type="button"：普通按钮，不会触发表单提交
                @click="clear"：点击时调用 clear 方法清空搜索条件
            -->
            <button type="button" @click="clear">清空</button>
        </form>

        <!--
            ============================================
            3. 数据表格 —— 展示从后端查回来的员工列表
            ============================================
        -->
        <table>
            <!-- 表头：写死的，不循环 -->
            <thead>
                <tr>
                    <th>序号</th>
                    <th>姓名</th>
                    <th>性别</th>
                </tr>
            </thead>
            <!-- 表体：用 v-for 循环渲染，有几个员工就生成几行 <tr> -->
            <tbody>
                <!--
                    v-for="(e, index) in empList" :key="e.id"
                    语法解释：
                    - empList 是 data 中的数组，存放所有员工数据
                    - 每次循环，e 代表当前员工对象，index 代表索引（从 0 开始）
                    - :key 是 Vue 循环时必须绑定的唯一标识，用于性能优化
                    - 这段代码相当于：遍历 empList，每遍历到一个员工就生成一行 <tr>
                -->
                <tr v-for="(e, index) in empList" :key="e.id">
                    <!-- index + 1，因为索引从 0 开始，序号从 1 开始 -->
                    <td>{{ index + 1 }}</td>
                    <td>{{ e.name }}</td>
                    <!--
                        e.gender 后端返回的是 1 或 2
                        1 表示男，2 表示女
                        用三元表达式转换成中文显示
                    -->
                    <td>{{ e.gender === 1 ? '男' : '女' }}</td>
                </tr>
            </tbody>
        </table>
    </div>

    <!--
        ============================================
        2. 引入 axios 库（用于发送 HTTP 请求）
           注意：必须放在 Vue 的 script 前面，否则 axios 未定义
        ============================================
    -->
    <script src="https://unpkg.com/axios/dist/axios.min.js"></script>

    <!--
        ============================================
        3. Vue 应用逻辑
           type="module"：使用 ES 模块方式加载 Vue
        ============================================
    -->
    <script type="module">
        // 从 CDN 导入 Vue 3 的 createApp 函数
        import { createApp } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js'

        // 创建一个 Vue 应用实例
        createApp({
            // ---------- data：数据 ----------
            // Vue 的响应式数据，数据变了，页面自动跟着变
            data() {
                return {
                    // 搜索表单的数据对象
                    searchForm: {
                        name: '',   // 搜索的姓名，初始为空
                        gender: '', // 搜索的性别，初始为空（不筛选）
                        job: ''     // 搜索的职位，初始为空（不筛选）
                    },
                    // 员工列表数组，初始为空，请求后端后填充数据
                    empList: []
                }
            },

            // ---------- methods：方法 ----------
            // 所有可调用的函数都写在这里
            methods: {
                /*
                 * getData()：发送 GET 请求，查询员工列表
                 * 执行时机：
                 *   1. 点击"查询"按钮（表单提交触发）
                 *   2. 点击"清空"按钮后自动调用
                 *
                 * 流程：
                 *   ① 拼接请求 URL，把 searchForm 里的三个字段作为查询参数
                 *   ② axios.get() 发送异步请求（Promise）
                 *   ③ .then()：请求成功，把后端返回的数据赋值给 empList
                 *   ④ .catch()：请求失败，打印错误信息
                 */
                getData() {
                    // 模板字符串拼接 URL，?name=xxx&gender=xxx&job=xxx
                    axios.get(`https://web-server.itheima.net/emps/list?name=${this.searchForm.name}&gender=${this.searchForm.gender}&job=${this.searchForm.job}`)
                        .then(res => {
                            // res 是 axios 包装后的响应对象
                            // res.data 是后端返回的 JSON 数据
                            // res.data.data 才是真正的员工列表数组
                            this.empList = res.data.data
                        })
                        .catch(err => {
                            // 请求失败时打印错误（比如网络断了、接口挂了）
                            console.log(err)
                        })
                },

                /*
                 * clear()：清空搜索条件，重新查询
                 * 流程：
                 *   ① 把 searchForm 重置为一个全新的空对象
                 *      （注意：不能修改属性值，Vue 3 中用新对象替换才能触发响应式更新）
                 *   ② 调用 getData() 重新请求所有数据（不带筛选条件）
                 */
                clear() {
                    // 用新对象替换旧对象，让 Vue 检测到变化
                    this.searchForm = {
                        name: '',
                        gender: '',
                        job: ''
                    }
                    // 重新查询，此时不带任何筛选条件
                    this.getData()
                }
            }
        }).mount('#app')
        // mount('#app')：把 Vue 应用挂载到 id="app" 的 DOM 元素上
        // 挂载后，Vue 会接管这个元素内部的所有内容
    </script>
</body>
</html>
```