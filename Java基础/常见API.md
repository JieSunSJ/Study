## API和API帮助文档
API:就是JDK提供的各种功能的Java类
API(Application Programming Interface):应用程序编程接口
简单理解:就是JDK提供的各种功能的Java类。我们不需要自己编写,直接使用即可。
这些类将底层的实现封装了起来,我们不需要关心这些类是如何实现的,只要学会如何使用。
API帮助文档:帮助开发人员更好的使用API和查询API的一个工具。
### 如何使用帮助文档
JDK.CHM
## 字符串概述
字符串的内容是不可变的,它的对象在创建后不能被更改
创建字符串的方式
```
// 1. 直接赋值
// 最简单 最常用
String s = "abc";
System.out.println(s);

//2.new+构造方法的方式创建字符串对象
// new+空参构造
String s1 = new String();
System.out.println(" -- " + s1 + "@@"); 

// 3. new+有参构造
// 根据传入字符串的内容,创建一个新的字符串对象
String s2 = new String(s); I
System.out.print1n(s2); // abc

//4. new+有参构造(字符数组)
char [] chs = {'a', 'b', 'c', 'd', 'e'};
String s3 = new String(chs);
System.out.print1n(s3);// abcde

//5. new+有参构造(字节数组)
// ASCII码表
// 97
// 98 --- 'b'
byte[] bytes = {97, 98, 99, 100, 101};
String s4 = new String(bytes);
System.out.print1n(s4); // abcde
```
两种方式的区别：
1.直接赋值的内存结构
每次直接赋值JVM会去堆内存的StringTable(串池)检查有没有这个串，没有就会创建，有的话就直接指向这个串
直接赋值:代码简单+串池复用，节约内存

new:每次都会创建一个新的字符串对象

## 字符串中常见成员方法
== 号比较的是什么？
基本数据类型比较的是数据值
引用数据类型比较的是地址值

字符串比较
```
boolean equals(要比较的字符串)//完全一样才是true，否则是false

boolean equalsIsIgnoreCase(要比较的字符串)//忽略大小写的比较
```

遍历字符串
```
public char charAt(int index):根据索引返回字符
str.charAt(0)//输出此位置的字符
public int length():返回此字符串的长度
数组的长度：数组名.length
字符串的长度：字符串对象.length()
```
快捷：str.length().fori+enter

字符串截取
```
String substring(int beginIndex,int endIndex)//截取
注意点：包头不包尾，包左不包右
只有返回值才是截取的小串
String substring(int brginIndex)截取到末尾
```

字符串替换
```
String replace(旧值，新值)//替换
把字符串中的旧值替换成新值，返回新值
```
更多的参考JDK.CHM

## StringBuilder
StringBuilder是字符串的一个工具类,可以让我们拼接字符串的时候效率更高
```
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 1000000; i++) {
sb.append("abc");
}
System.out.println(sb);
//如果不用这个时间会有点久
```
StringBuilder append(任意类型):添加数据
StringBuilder reverse():反转容器中的内容
int length():返回长度(字符的个数)
String toString():转回String字符串对象
拼接过后最好在toString()赋值一下，毕竟这是个容器

## 集合
数组的弊端：一旦定义，长度不可变
集合：是一种长度可变的容器
```
boolean add(E e)//添加数据
void add(int index, E e)//添加数据
boolean remove(E e)//删除元素
E remove(int index)//删除元素
E set(int index,E e)//修改元素
E get(int index)//获取元素
int size()//集合长度
```
判断是否相等用equ
集合里面只能存引用数据类型，如果是基本数据类型会自动转换为相应的类
```
基本类型
byt
short
int
long
float
double
char
boolean
包装类
Byte
Short
Integer
Long
Float
Double
Character
Boolean
```
