官网：
```
https://spring.io
```
Spring发展到今天已经形成了一种开发生态圈,Spring提供了若干个子项目,每个项目用于完成特定的功能。
Spring Framework是底层框架
由于Spring 配置繁琐入门难度大,官方推出了SpringBoot,其简化配置快速开发
## 入门程序
需求:基于SpringBoot开发一个Web应用,浏览器发起请求/hello之后,给浏览器返回一个字符串"Hello Xxx"。
```
1. 创建springboot工程,并勾选web开发相关依赖。
2. 定义HelloController类,添加方法 hello,并添加注解。
```
![[Pasted image 20260812172808.png]]
勾选Spring Web
![[Pasted image 20260813090124.png]]
入门程序：
```
package cn.hytc.springbootweb;  
  
import org.springframework.web.bind.annotation.RequestMapping;  
import org.springframework.web.bind.annotation.RestController;  
  
@RestController  
public class HelloController {  
    @RequestMapping("/hello")  
    public String hello(String name) {  
        return "hello " + name;  
    }  
}
```
![[Pasted image 20260813092228.png|624]]
## Spring官方脚手架连接不上解决方案
![[Pasted image 20260813092448.png]]
## 为什么只需要运行启动类就可以启动web
因为当初创建的时候勾选了springweb这个依赖，然后由于maven的依赖传递，引入了tomcat的依赖，这个是springweb的内嵌tomcat,tomcat就相当于一个web服务器，启动启动类就会运行tomcat
所以使用springboot就可以不用配置tomcat，因为依赖里面内嵌了一个tomcat
