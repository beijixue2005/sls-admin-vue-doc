## 说明
目前权限功能暂时用动态路由模拟了一下，参考地址:[https://github.com/sls-admin/sls-admin-vue/releases](https://github.com/sls-admin/sls-admin-vue/releases)

目前只是模拟实现，并没有后端案例，因为重点就是前段怎么实现动态路由，以及前段需要的数据格式，确定了这两个因素，至于后台要怎么存，完全随意，不限制。

> 真实的权限交互，正在开发中...

## 流程
### 重新组装组件结构
为了方便，需要重新把组件的结构给组织下，看下src/views/目录结构
```
├── src                        // 源代码
│   ├── views                 // 视图
│       ├── index.js                 // 负责导出所有视图
│       ├──container                 // 路由容器组件
│               ├──Home.vue                 // 一级路由容器组件
│               ├──Content.vue                // 二级路由容器组件
│               ├──index.js                 // 入口文件
│       ├──page                 // 所有页面
│               ├──adv                 // 高级模块
│               ├──function                // 功能模块
│               ├──......
│               ├──index.js                 // 入口文件
│       ├──login                 // 登录
```

src/views/index.js内容如下:
```javascript
import Home from './container/Home.vue';
import Content from './container/Content.vue';
import Page from './page/';

export default {
	Home,
	Content,
	Page
};
```
**注意:不要导入登录组件，不然可能会造成循环引用错误。**
**注意:不要导入登录组件，不然可能会造成循环引用错误。**
**注意:不要导入登录组件，不然可能会造成循环引用错误。**
这里导出的是个对象，包含了一级路由容器，二级路由容器，以及所有的页面组件，通过打印出来可以看到最终的对象结构是如下这样的
```javascript
{
    Home,
    Content,
    Page:{
        Function:{
                Open:{
                    List,
                    Form,
                    Vuex,
                    Test404,
                    Echarts
                    ......
                },
                ......
        },
        ......    
    }    
}
```
组装成这样的结构是为了方便转换动态路由。

## 模拟动态路由
所谓模拟动态路由，就是模拟一下后台返回的路由，这个结构肯定是由我们前端来定，毕竟路由是属于前端的。
模拟后台返回的路由数据在**src/async-router**文件夹，通过查看源码可以看到，里面定义的数据结构基本上和路由是一模一样，只是在路由对象中多了**component_name**和**component_path**两个属性，并且**没有了component属性**，通过下面实际的代码解释:
#### src/async-router/function/index.js:
```javascript
import open from './open';

export default {
	path          : '/function',
	name          : '静态演示',
	icon          : 'inbox',
	component_name: 'Home',
	component_path: 'Function',
	redirect      : '/function/open',
	children      : [open]
};
```
#### src/async-router/function/open.js:
```javascript
export default {
	path          : 'open',
	name          : '公共内容',
	icon          : 'inbox',
	component_name: 'Content',
	component_path: 'Open',
	redirect      : '/function/open/echarts',
	children      : [{
		path          : 'echarts',
		name          : '图表',
		icon          : 'bar-chart',
		component_name: 'Echarts',
	}, {
		path          : 'list',
		name          : '列表',
		icon          : 'reorder',
		component_name: 'List',
	}, {
		path          : 'form',
		name          : '表单',
		icon          : 'edit',
		component_name: 'Form',
	}, {
		path          : 'vuex',
		name          : 'Vuex',
		icon          : 'window-restore',
		component_name: 'Vuex',
	}, {
		path          : 'test404',
		name          : '测试404',
		icon          : 'window-restore',
		component_name: 'Test404',
	}]
};
```

先解释component_name吧，component_name就是组件的名称，我会拿到到视图对象里面去找component_name的属性，如果找到，就把组件赋值给这个路由对象。

所以在一级路由和二级路由上面，分别定义Home和Content，那么自然就会到视图里面 找到这两个，这没问题。

但是看三级路由，三级路由定义的组件名称，这个东西如果直接定义成这样是无法找到的，因为这些组件都会有一个父级去承载他们，我又不知道他们的父级是什么，所以怎么找呢？

再看一级和二级路由，一级路由和二级路由多了一个**component_path**属性，这两个属性的值是有规律的。

一级的属性值是**Function**,二级的属性值是**Open**，这两个东西和哪里有关联呢？再回到视图对象，看下最终的结构，可以理解为所有的组件都存在Page属性中。

而格式就是:
**视图对象["Page"][模块名(Function)][菜单名(Open)][组件名(List/Form/Test404/....)]**

所以:
* 模块名就是一级路由定义的component_path的值，
* 菜单名就是二级路由定义的component_path的值
* 组件名就是三级路由定义的component_name的值

> 总结:一级和二级的component_path的定义就是为了可以找到三级的component_name而存在。
