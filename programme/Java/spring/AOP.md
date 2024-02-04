# AOP

AOP "Aspect Oriented Programming"的缩写 意为: 面向切面编程

AOP 是 OOP 的延续

利用 AOP 可以对业务逻辑的各个部分进行隔离，从而使得业务逻辑各部分之间的耦合度降低，提高程序的可重用性，同时提高了开发的效率

**“不修改源代码的条件下，增强业务”**

## AOP 底层原理

1、AOP 底层使用动态代理

​	（1）有两种情况动态代理：

​			  第一种 有接口情况，使用 JDK 动态代理：

​				**创建接口实现类代理对象，增强类的方法**

```java
interface UserDao {
    public void login();
}
class UserDaoImpl implements UserDao {
    public void login() {
        // 登录实现过程
    }
}
```

​				在 JDK 动态代理中，创建 UserDao 接口实现代理对象，通过代理对象替换被代理对象。

​			 第二种 没有接口情况，使用 CGLIB 动态代理：

​				**CGLIB 动态代理：通过创建当前类子类的代理对象，增强类的方法**

```java
class User {
    public void add() {
    	.....   
    }
}

// 第一种，增强 User 功能的方法（最原始的方式）
class Person extends User {
    // 继承 User 类，去重写 User 的方法，进行业务增强
    public void add() {
        super.add();
        // 增强逻辑
    }
}
```



## AOP——JDK 动态代理实现

使用 JDK 动态代理，使用 Proxy 类（java.lang.reflect）里面的方法创建代理对象

（1）调用 newProxyInstance 方法

​			static Object newProxyInstance(Classloader loader, Class<?> interfaces, InvocationHandler h)

​			返回指定接口的代理类的实例，该接口将方法调用分派给指定的调用处理程序。

​			

​			Classloader loader 该类的类加载器

​			Class<?> interfaces 增强方法所在的类，这个类实现的接口，支持多个接口

​			InvocationHandler h 实现这个接口 InvocationHandler 创建代理对象，写增强的方法

（2）JDK 动态代理 实例

​			1、创建接口，定义方法

```java
package proxy;

public interface UserDao {

    public int add(int a, int b);

    public String update(String id);
}

```

​			2、创建接口实现类，实现方法

```java
package proxy;

public class UserDapImpl implements UserDao{

    @Override
    public int add(int a, int b) {
        return a+b;
    }

    @Override
    public String update(String id) {
        return id;
    }
}

```

​			3、实现 InvocationHandler 接口，也就是中介，做业务增强的

​					当代理对象，调用方法时（任何方法），都是先触发 InvacationHandler 的 invoke 方法

​					对应参数分别为

​						method：当前代理对象，所调用的方法名

​						args：当前代理对象，调用方法是，传递的参数

​						return：返回是这个 invoke 反射得到的结果，也就是invoke()的返回值

​			4、再通过 Proxy.newProxyInstance 得到代理对象

```java
package proxy;

import java.lang.reflect.InvocationHandler;
import java.lang.reflect.Method;
import java.lang.reflect.Proxy;
import java.util.Arrays;

public class JDKProxy {
    public static void main(String[] args) {
        // 创建接口实现类代理对象
        Class[] interfaces = {UserDao.class};
        UserDao userDao = new UserDaoImpl();
        // newProxyInstance 返回的是 Object 类，需要向下转型才能使用 UserDao 的方法
        UserDao dao = (UserDao) Proxy.newProxyInstance(JDKProxy.class.getClassLoader(), interfaces, new UserInHandler(userDao));
        int i = dao.add(1, 2);
        System.out.println("result: "+i);
    }
}
class UserInHandler implements InvocationHandler {
    // 1 创建是谁的代理对象，就把谁传进来
    // 有参数构造传递
    private Object object;  // 这里为了写的通用一些，所以使用Object，在这里我们代理的是UserDao
    public UserInHandler(Object object) {
        this.object = object;
    }
    @Override
    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
        // 方法之前
        System.out.println("方法之前执行...."+"方法名:"+method.getName()+"&传递的参数:"+ Arrays.toString(args));
        // 被增强的方法执行
        Object invoke = method.invoke(object, args);// 调用方法可能有返回值
        // 方法之后
        System.out.println("方法之后执行...."+object);
        return invoke;    // 将返回值返回
    }
}
```

## AOP 术语

1、连接点

​	类里面哪些方法可以被增强，这些方法称为连接点

2、切入点

​	实际被真正增强的方法，称为切入点

3、通知（增强）

​	（1）实际增强的逻辑部分称为通知

​	（2）通知有多种类型

​				前置通知，后置通知，环绕通知，异常通知，最终通知

4、切面

​	是一个动作、过程

​	把通知应用到**切入点**的过程就叫做切面

​	

## AspectJ

Spring 框架一般都是基于 AspectJ 实现 AOP 操作

（1）什么是AspectJ？

​		AspectJ 不是 Spring 组成部分，独立 AOP 框架，一般把 AspectJ 和 Spring 框架一起使用，进行 AOP 操作

（2）基于AspectJ实现AOP操作

​		基于xml配置文件实现

​		基于注解方式实现（使用）

@Before

@After

...