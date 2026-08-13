### 配置Maven(全局)
![[Pasted image 20260812095654.png]]
![[Pasted image 20260812095906.png]]
![[Pasted image 20260812100006.png]]
Java编译器的版本也要配置一下，这里是全局配置
![[Pasted image 20260812100109.png]]

### 创建集成Maven
先创建一个空项目，然后设置里面更改jdk版本，然后右键项目创建java-maven模块
现在的Idea创建java项目时测试目录里面一般不带配置文件，可以自己手动创建
运行HelloWorld,左侧会出现target文件，里面是编译好的字节码文件和jar包文件

## Maven坐标
### 什么是坐标?
Maven 中的坐标是资源(jar)的唯一标识,通过该坐标可以唯一定位资源位置。
使用坐标来定义项目或引入项目中需要的依赖。
### Maven 坐标主要组成
```
groupId:定义当前Maven项目隶属组织名称(通常是域名反写,例如:com.itheima)
artifactId:定义当前Maven项目名称(通常是模块名称,例如 order-service、goods-service)
version:定义当前项目版本号
	-SNAPSHOT:功能不稳定、尚处于开发中的版本,即快照版本
	-RELEASE:功能趋于稳定、当前更新停止,可以用于发行的版本
```
## 导入Maven项目
方式一:File ->Project Structure ->Modules -> Import Module ->选择maven项目的pom.xml。
方式二:Maven面板 ->+(Add Maven Projects) ->选择maven项目的pom.xml
	先将maven项目文件夹在资源管理器里面放进去，然后导入对应的pom.xml
