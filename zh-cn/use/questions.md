## 无法登陆

确认以及肯定按照 [快速启动](/zh-cn/use/start.md ":target=_blank") 正确操作？确认请往下看：

打开浏览器，访问：[http://api.slsadmin.org/login/login](http://api.slsadmin.org/login/login ":target=_blank")

> 正常情况，会出现如下图，这代表外网接口正常，是你配置有问题，请检查是否因为自己修改代码错误导致。

![测试请求](/static/images/use/test-request.png)

如果无法请求，或请求异常，直接找我即可。



## js导入导出报错

错误如下图：
![模块导入导出报错](/static/images/module-error.png)

这个错误是因为导入导出混用问题，简单地说就是：一个文件里面，要么是import和export，要么是require和module.exports。不能用import导入，module.exports导出；同理，也不能使用require导入，用export导出。

我在做这个项目的时候，vue-cli以及webpack版本都相对比较低，还可以把import和module.exports混用，现在新版本不能这样搞了，规定import和export一起使用，require和module.exports一起使用。

所以为了解决这个问题，在第一版更新完，将会用最新的vue-cli以及webpack重新构建一次，目前大家先自行解决这个问题。

> **目前此问题已不存在。**