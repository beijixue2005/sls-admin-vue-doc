## 目录结构
```shell
├── build                      // 构建相关  
├── config                     // 配置相关
├── src                        // 源代码

│   ├── libs                   // 全局第三方库
│   ├── assets                 // 主题 字体等静态资源
│   ├── components             // 全局公用组件
│   ├── layout                 // 布局组件
│   ├── config                 // 全局配置

│   ├── register                 // 全局注册入口

│   ├── apis                   // 所有的接口定义
│   ├── utils                  // 全局工具集

│   ├── directives              // 全局指令
│   ├── filters                 // 全局过滤器
│   ├── mixins                  // 全局混合

│   ├── router                 // 路由
│   ├── store                  // 全局store管理

│   ├── views                   // 所有的页面组件

│   ├── App.vue                // 入口页面
│   └── main.js                // 入口 加载组件 初始化等
├── static                     // 第三方不打包资源
├── .babelrc                   // babel-loader 配置
├── eslintrc.js                // eslint 配置项
├── .gitignore                 // git 忽略项
├── favicon.ico                // favicon图标
├── index.html                 // html模板
└── package.json               // package.json

```