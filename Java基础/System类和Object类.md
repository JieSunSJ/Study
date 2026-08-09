## System类
System也是一个工具类,提供了一些与系统相关的方法
```
public static void exit(int status)//终止当前运行的 Java 虚拟机
public static long currentTimeMillis()//返回当前系统的时间(毫秒值形式)
public static void arraycopy(数据源数组,起始索引,
目的地数组,起始索引,拷贝个数)//数组拷贝
```
currentTimeMillis()返回的值是从从1970年1月1日 8:0:0到现在为止的毫秒值
可以在程序开始和末尾分别记录，最后相减就是程序的运行时间
```
//源数组
int[] arr1 = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
// 目标数组
int[] arr2 = new int[10];
// 数组的拷贝
System.arraycopy(arr1I srcPos: 0,arr2, destPos: 0, length: 10);
for (int i = 0; i < arr2.length; i++) {
System.out.print1n(arr2[i]);
}
```

## Object
Object是Java中的顶级父类,所有的类都直接或间接的继承于Object类
```
public String toString()//返回对象的字符串表示形式
public boolean equals(Object obj)//比较两个对象是否相等
```
用toString返回类的时候会把类的内存地址返回，不是我们想要的，所以一般在JavaBean里面要重写toString方法
如果想要把一个对象变成字符串并打印,其实不需要手动调用toString方法,直接打印这个对象就可以了

解释输出语句真正的含义:
System: Java中已经写好的一个工具类,表示系统
out:是System里面的一个静态变量,默认初始化值为null,程序启动之后,会进行赋值,记录控制台的对象,所以在打印的时候会把数据打印在控制台上
println:方法内部调用了toString()方法

equals()在Object类下实际比较的还是内存地址，只不过String类等对其进行的重写
当我们要对两个类的对象值进行比较的时候，要重写toString()方法

