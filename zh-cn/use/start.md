### 启动必看

项目开源在GitHub，可以使用git克隆下来

```
git clone https://github.com/sls-admin/sls-admin-vue.git
cd sls-admin
npm/cnpm install
```

完事之后，打开`/config/index.js`，找到如下：

```
proxyTable: {
    '/slsAdminApi': {
        target: 'http://slsadmin.api.sls.com',
        changeOrigin: true,
        pathRewrite: {
            '^/slsAdminApi': ''
        }
    }
},
```
修改为如下：

```
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

然后运行如下命令demo就启动起来了。

```
npm run dev
```

> **注意：如果你是先启动的项目，后修改的这个配置，你需要重启启动webpack-dev-server，也就是Ctrl/Cammand+C终止，重新运行上面命令即可。**

