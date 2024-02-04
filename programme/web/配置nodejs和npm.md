# 配置nodejs和npm

## 一、下载nodejs

官网地址：[nodejs](https://nodejs.org/en/download/)

该安装包在windows下有2中形式

- **.msi的安装
- **.zip的安装

### 1.nodejs(msi)方式的安装

下载完成后，双击"node-v10.15.3-x64.msi"，开始安装Node.js

### 2.nodejs(zip)方式的安装

直接解压

## 二、环境配置

### 1.引言

**传统方法总结:**

1. npm包全局目录：`C:/Users/[username]/AppData/Roaming/npm/node_modules`
2. npm包全局命令目录：`C:/Users/[username]/AppData/Roaming/npm`
3. npm实际去找全局命令的目录：`C:/Users/[username]/.npmrc`文件内容的`prefix`值
4. npm包全局cache目录：`C:/Users/[username]/.npmrc`文件内容的`cache`值
5. 需要配置系统环境变量：计算机 -> 属性 -> 高级系统配置 -> 环境变量 -> `Path/NODE_Path`...

### 2.修改Node.js的配置

1. node安装目录

```
安装node到[D:/node]下
```

2. 修改默认的全局目录


​	方法一：到node安装目录[D:/node]执行以下命令：

```
npm config set prefix D:/node/nodejs/node_global/ //全局包目录，就在node安装目录新建了个nodejs文件夹存放
npm config set cache D:/node/nodejs/node_cache/ //全局包缓存目录，就在node安装目录新建了个nodejs文件夹存放
```

​	方法二：直接修改`C:/Users/[username]/.npmrc`文件的`cache`值和`prefix`值，文件如下：

```
prefix=D:\node\nodejs\node_global
cache=D:\node\nodejs\node_cache
registry=https://registry.npm.taobao.org/
```

3. 配置环境变量

​	计算机 -> 属性 -> 高级系统配置 -> 环境变量 -> 用户变量 -> 编辑`Path`，添加`global`目录如下：

```
Path: D:\node\nodejs\node_global\;
```

​	计算机 -> 属性 -> 高级系统配置 -> 环境变量 -> 系统变量 -> 编辑`Path`，添加`modules`目录如下：

```
Path: D\node\nodejs\node_global\node_modules
```

## 三、nmp设置淘宝镜像

### 1.设置npm为淘宝镜像

```
npm config set registry https://registry.npm.taobao.org/
```

### 2.设置cnmp为淘宝镜像

```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

### 3.验证是否配置生效

```
npm config get registry
cnpm config get registry
```

### 4.切换为官方的镜像

```
npm config set registry https://registry.npmjs.org/
```

