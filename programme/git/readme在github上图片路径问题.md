# README在GitHub上图片路径问题

在github中，可以将图片放在项目下，一起push到github上，一般有如下两种方法：

（1）超链接：`https://raw.githubusercontent.com/用户名/项目名/master/图片文件夹/XXX.png`

```
![img](https://raw.githubusercontent.com/用户名/项目名/master/图片文件夹/XXX.png)
```

（2）相对路径，<font color='crimson'>注意：这里一定要是“/”，而不能是“\”。如果是“\”，那么在github中，会将其转义了，导致图片读取失败。</font>

```
![img](floder/XXX.png)
```
