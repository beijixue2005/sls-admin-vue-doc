# 接口配置
> 很多人不理解在登录组件中，写的$$api_user_login是怎么出来的，下面就以这个做解释。

### 以定义用户模块的接口为例
```shell
├── src                        // 源代码
│   ├── apis                 // 接口
│       ├── index.js                 // 负责导出所有模块接口
│       ├──user                 // 用户模块接口
│           ├──index.js                // 负责导出该模块下所有的接口
```
首先看apis下的index.js内容，只保留了user相关的内容，方便看的更清楚
```js
import user from './user/';
export default [
    {
        module:'user',
        name:'用户管理',
        list:user
    }
];
```
既然上面导入了user模块，那再看下user模块下的index.js内容
```js
export default [
    {
        name  : '登录',
        method: 'login',
        path  : '/login/login',
        type  : 'post',
    },
    {
        name  : '注册',
        method: 'register',
        path  : '/User/register',
        type  : 'post',
    }
];
```
> - apis/index.js中导出了一个数组，数组中每个元素是一个对象，对象有一个属性叫module,此属性值就是$$api_user_login中的user的由来。
> - 模块下的index.js中也导出了一个数组，数组中每个元素也是一个对象，对象有一个属性叫method,此属性值就是$$api_user_login的login的由来。
> - $$api怎么来的呢？这个是在注册机制里面定义的，这里不做太多解释。
> - 反正意思就是，这里面定义的接口，通过$$api_moduleName_methodName就可以调用到。