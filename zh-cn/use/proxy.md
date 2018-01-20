## 代理介绍

#### 很多人对代理不是很明白，我先解释一下为什么要代理？什么是代理？

> 为什么要代理？

前端ajax跨域，如果请求的接口域名，和你当前所在域名，不是一个域名时，浏览器上出现跨域问题。
那么解决跨域的方式也有多种，常见的让后台设置允许跨域，还有一种方式是前端设置代理。
举个例子，以我们的项目为例：
项目启动后，我们的前端地址host是localhost:8090，而我线上的接口是slsadmin.api.sailengsi.com
正常请求的话，明显存在跨域了。

> 什么是代理

所以，通过这种代理手段，设置一个虚拟路径，当检测请求的路径是这个虚拟路径时，自动帮我们转发到我们的真实地址，这样一来，浏览器上看到的请求地址就是设置的虚拟路径，实际上请求的确实真实的地址，就不存在跨域了。

## 开发模式

> 开发模式，就是`npm run dev`时，通过`webpack-dev-server`启动的服务来开发

比如当前的项目，在登录时请求的明明是
```
http://localhost:8090/slsAdminApi/Login/login
```
但是为什么会正常执行我服务器的接口呢？
这就是因为，用`webpack`做了代理设置，设置的地方在`/config/index.js`，核心在如下
```javascript
proxyTable: {
    '/slsAdminApi': {
        target: 'http://api.slsadmin.org',
        changeOrigin: true,
        pathRewrite: {
            '^/slsAdminApi': ''
        }
    }
},
```
上面代码中的`/slsAdminApi`，就是在根路径下面设置的一个虚拟路径，而target值就是转发的地址。
所以，当访问的URL是 `http://localhost:8090/slsAdminApi/xxx`时， 代理会自动帮我们把地址中的 `http://localhost:8090/slsAdminApi` 替换成 `http://api.slsadmin.org` ，并且浏览器看到的依然是`http://localhost:8090/slsAdminApi/xxx` 开头，从而解决了跨域问题。

所以请求 `http://localhost:8090/slsAdminApi/Login/login` 时，实际上请求的是 `http://api.slsadmin.org/Login/login`,就是这么回事。
 
其实这只是代理的一种，叫反向代理，那么对应的还有正向代理，更多知识，请自行查询。

## 部署模式

> 部署模式，实际上访问的是`npm run build`之后生成的`dist`中的内容

部署模式访问，是访问的线上的服务器，Nginx或者Apache，或者IIS，或者其他。
所以这个时候，和我们的`webpack`代理就没有关系了。

此时，在访问 `域名/代理的路径/xxx`时，就会出现`404`，因为这是个虚拟路径。

比如项目中设置的根路径是/slsAdminApi，本地开发模式，通过webpack搞定了代理。
那么线上就需要通过服务器配置文件去设置代理了。

我个人服务是用的Nginx，下面以我的为例
```shell
location /slsAdminApi/
{
	proxy_pass https://slsadmin.api.sailengsi.com/;
}
```
这个配置是在项目域名vhost配置中加。

其他服务暂时没接触过，可自行查询。

# 实战操作

下面来模拟一个真正的场景，可能你会理解的更快一些。

> 开发模式

假设你当前项目信息如下：
- 接口根地址：  `http://localhost/admin/`
- 登录接口地址：`http://localhost/admin/Login/login`

然后假设我们想要代理的路径加入是/cmsAdminApi，我们需要把`/config/index.js`中的代码：
```javascript
proxyTable: {
    '/slsAdminApi': {
        target: 'http://slsadmin.api.sailengsi.com',
        changeOrigin: true,
        pathRewrite: {
            '^/slsAdminApi': ''
        }
    }
},
```
改成如下：
```javascript
proxyTable: {
    '/cmsAdminApi': {
        target: ' http://localhost/admin/',
        changeOrigin: true,
        pathRewrite: {
            '^/cmsAdminApi': ''
        }
    }
},
```

改完之后，启动服务，`npm run dev`，如果已经启动，需要重启才行。
最后你测试一下接口，当请求是  `/cmsAdminApi/Login/login`，就能成功的请求到`http://localhost/admin/Login/login` 了。

> 部署模式

最后把`npm run build`之后的`dist`内容，放到服务器，然后服务器配置增加下代理配置，参考上一节部署模式。