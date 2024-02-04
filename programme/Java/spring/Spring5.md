## Spring5

### IOC 容器

**IOC 操作 Bean 管理（概念）**

1、什么是 Bean 管理

​	（1）、Spring 创建对象

​	（2）、Spring 注入属性

2、Bean 管理操作有两种方式

​	（1）、基于 xml 配置文件方式实现

​	（2）、基于注解方式实现



**IOC 操作 Bean 管理（基于 xml 方式）**

1、基于 xml 方式

```xml
<!--1 配置User对象创建-->
<bean id="user" class="com.atguigu.spring5.User"></bean>
```

​	（1）、在 Spring 配置文件中，使用 bean标签，标签里面添加对应属性，就可以实现对象创建

​	（2）、在 bean 标签有很多属性，介绍常用的属性

​			id：唯一标识

​			class：类的全路径

​			name：别名，可以使用特殊字符（现在已经被 id 代替了）

​	（3）、创建对象时候，默认也是执行无参数构造方法

2、基于 xml 方式注入属性

​	（1）、DI：依赖注入，就是注入属性



3、第一种注入方式：使用 set 方法进行注入

​	（1）、创建类，定义属性和对应的 set 方法

```java
public class Book{
    
    // 创建属性
    private String bname;
    private String bauthor;
    
    // 创建属性对应的 set 方法
    public void setBname(String bname) {
        this.bname = bname;
    }
    public void setBauthor(String bauthor) {
        this.bauthor = bauthor;
    }
}
```

​	（2）、在 Spring 配置文件中配置对象创建，配置属性注入

```xml
<!--2 set方法注入属性-->
<bean id="book" class="com.atguigu.spring5.Book">
	<!--使用 propertiy 完成属性注入
		name：类里面属性名称
		value：向属性注入的值
	-->
    <property name="bname" value="流浪地球"></property>
    <property name="bauthor" value="刘慈恩"></property>
</bean>
```

4、第二种注入方式：通过有参数的构造器进行注入

