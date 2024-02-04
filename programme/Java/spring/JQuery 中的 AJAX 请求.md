## JQuery 中的 AJAX 请求

```java
package com.example.AJAXDemo;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.lang.reflect.InvocationTargetException;
import java.lang.reflect.Method;

public class BaseServlet extends HttpServlet {

    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {

        try {
            String action = req.getParameter("action");
            Class<? extends BaseServlet> aClass = this.getClass();
            Method method = aClass.getDeclaredMethod(action, HttpServletRequest.class, HttpServletResponse.class);
            method.invoke(this,req,resp);
        } catch (NoSuchMethodException e) {
            e.printStackTrace();
        } catch (InvocationTargetException e) {
            e.printStackTrace();
        } catch (IllegalAccessException e) {
            e.printStackTrace();
        }
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req,resp);
    }
}

```



### $.ajax 方法

​	url									表示请求的地址

​	type								 表示请求的类型 GET或POST 请求

​	data								 表示发送给服务器的数据

​								格式有两种：

​									一、name=value&name=value

​									二、{key:value}，最后会被解析成第一种

​	success							请求成功，响应的回调函数

​	dataType						 服务器返回的数据类型（响应的数据类型）

​								常用的数据类型有: 

​									text 表示纯文本

​									xml 表示xml数据

​									json 表示json对象

```javascript
$(function(){
    // ajax 请求
    $("#ajaxBtn").click(function (){

        $.ajax({
            url:"http://localhost:8080/AJAXDemo_war_exploded/ajaxServlet",
            data:"action=jQueryServlet",
            type:"GET",
            success:function (data){
                // 这里的响应成功必须要有一个参数，作用相当于原生ajax请求里的XMLHttpRequest.responseText
                // alert("服务器返回的数据是： "+data);
                let jsonObj = JSON.parse(data);

                $("#msg").html(" ajax 编号: "+jsonObj.id+",姓名: "+jsonObj.name);
            },
            dataType:"text"
        })
    })
})
```



### $.get 方法和 $.post 方法

​	url									待载入页面的URL地址

​	data								 待发送 key/value 参数

​	callback							载入成功时回调函数

​	type								  返回内容格式，xml、html、script、json、text、_default

$.get

```javascript
// ajax-get 请求
$("#getBtn").click(function (){
    // url,data,callback.type
    $.get("http://localhost:8080/AJAXDemo_war_exploded/ajaxServlet","action=jQueryGet",function (data){
        $("#msg").html(" get 编号: "+data.id+",姓名: "+data.name)
    },"json");
})
```

$.post

```javascript
// ajax-post 请求
$("#postBtn").click(function (){
    // url,data,callback.type
    $.post("http://localhost:8080/AJAXDemo_war_exploded/ajaxServlet","action=jQueryPost",function (data){
        $("#msg").html(" post 编号: "+data.id+",姓名: "+data.name)
    },"json");
})
```





### $.getJSON 方法: 通过 HTTP GET 请求载入 JSON 数据

​	请求类型是固定的（GET），返回数据类型也是固定的（JSON）

​	url									

​	data

​	callback

```javascript
// getJSON请求
$("#jsonBtn").click(function (){

    $.getJSON("http://localhost:8080/AJAXDemo_war_exploded/ajaxServlet","action=getJSON",function (data){
        $("#msg").html(" getJSON 编号: "+data.id+",姓名: "+data.name)
    })
})
```



### 表单序列化 serialize()

​	serialize() 可以把表单中所有表单项的内容都获取到，并以 name=value&name=value的形式进行拼接

```html
<form id="form01">
    用户名:<input name="username" type="text"> <br>
    密码:<input name="password" type="password"> <br>
</form>
<button id="submit">提交--serialize</button>
```

```javascript
// serialize()
$("#submit").click(function (){
    // 把参数序列化

    // alert($("#form01").serialize())

    $.getJSON("http://localhost:8080/AJAXDemo_war_exploded/ajaxServlet","action=jQuerySerialize&" + $("#form01").serialize(),function (data){
        $("#msg").html(" serialize 编号: "+data.id+",姓名: "+data.name)
    })
})
```

