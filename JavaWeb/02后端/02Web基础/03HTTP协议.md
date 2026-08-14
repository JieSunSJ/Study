```
http://localhost:8080/hello?name=?
```
网址前面带有http,这个就是协议部分
概念:Hyper Text Transfer Protocol,超文本传输协议,规定了浏览器和服务器之间数据传输的规则。
http响应格式
![[Pasted image 20260813094714.png]]
```
特点:
1. 基于TCP协议:面向连接,安全
2. 基于请求-响应模型的:一次请求对应一次响应
3. HTTP协议是无状态的协议:对于事务处理没有记忆能力。每次请求-响应都是独立的。
缺点:多次请求间不能共享数据。
· 优点:速度快
```
## HTTP请求协议
![[Pasted image 20260813105838.png]]
### 请求数据格式
请求行里面的HTTP后面的数字是HTTP的版本
![[Pasted image 20260813095709.png]]
```
请求行:请求数据第一行(请求方式、资源路径、协议)
请求头:第二行开始,格式key:value
请求体:POST请求,存放请求参数
```

```
请求方式-GET:请求参数在请求行中,没有请求体,如:/brand/findAll?name=OPPO&status=1。GET请求大小在浏览器中是有限制的。
请求方式-POST:请求参数在请求体中,POST请求大小是没有限制的。
```
### 请求数据获取
Web服务器(Tomcat)对HTTP协议的请求数据进行解析,并进行了封装(HttpServletRequest),在调用Controller方法的时候传递给了该方法。这样,就使得程序员不必直接对协议进行操作,让Web开发更加便捷。
```
package cn.hytc.springbootweb;  
  
import jakarta.servlet.http.HttpServletRequest;  
import org.springframework.web.bind.annotation.RequestMapping;  
import org.springframework.web.bind.annotation.RestController;  
  
@RestController  
public class ResquestController {  
    @RequestMapping("/request")  
    public String request(HttpServletRequest request) {  
        //获取请求方式  
        String method = request.getMethod();  
        System.out.println("请求方式:" + method);  
        //获取请求url  
        String url = request.getRequestURL().toString();  
        System.out.println("请求url:" + url);  
        //获取请求协议  
        String protocol = request.getProtocol();  
        System.out.println("请求协议:" + protocol);  
        //获取请求参数 -name age        String name = request.getParameter("name");  
        System.out.println("请求参数:" + name);  
        //获取请求参数 -age        String age = request.getParameter("age");  
        System.out.println("请求参数:" + age);  
        //获取请求头  
        String header = request.getHeader("Content-Type");  
        System.out.println("请求头:" + header);  
        //获取请求体  
        try {  
            String body = new String(request.getInputStream().readAllBytes());  
            System.out.println("请求体:" + body);  
        } catch (Exception e) {  
            e.printStackTrace();  
        }  
        return "OK";  
    }  
  
}
```
输入：
```
http://localhost:8080/request?name=admin&age=18
```
结果：
```
请求方式:GET
请求url:http://localhost:8080/request
请求协议:HTTP/1.1
请求参数:admin
请求参数:18
请求头:null
请求体:
```
## HTTP响应协议
### 响应数据格式
![[Pasted image 20260813105811.png]]
```
响应行:响应数据第一行(协议、状态码、描述)
响应头:第二行开始,格式key:value
响应体:最后一部分,存放响应数据
```
![[Pasted image 20260813110531.png]]
请求不对会设置307进行重定向
![[Pasted image 20260813121319.png]]
### 响应数据设置
Web服务器对HTTP协议的响应数据进行了封装(HttpServletResponse),并在调用Controller方法的时候传递给了该方法。这样,就使得程序员不必直接对协议进行操作,让Web开发更加便捷。
方式一:基于HttpServletResponse封装
```
//方式一:使用HttpServletResponse响应对象  
@RequestMapping("/response")  
public void response(HttpServletResponse response) throws IOException {  
    response.setStatus(401);  
    response.setHeader("name", "javaweb-ai");  
    response.getWriter().write("<h1>hello</h1>");  
}
```
方式二:基于ResponseEntity封装
```
//方式二:使用ResponseEntity注解  
@RequestMapping("/response2")  
public ResponseEntity<String> response2() {  
    return ResponseEntity.status(401).header("name", "javaweb-ai").body("<h1>hello</h1>");  
}
```