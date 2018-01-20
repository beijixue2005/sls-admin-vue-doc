## 基本流程

- 肯定是加载入口文件main.js
    - 初始化路由
    - 初始化store
    - 自动注册机制，核心代码是`import 'register/';`

## 注册机制
> 注册，看下register/index.js内容,以注册全局组件为例

```js
import cps from './component.js';
_.each(cps, (item, key) => {
	var cp_name=key.replace(/([A-Z])/g,"-$1").toLowerCase();
	if(cp_name && cp_name[0]==='-'){
		cp_name=cp_name.replace('-','');
	}
    Vue.component(cp_name, item);
});
```
> 组件从定义，到注册之间，还有一个中转站，也就是上面看到的component.js，看下内容

```js
import {ListData,FormData,DialogInfo,Echarts} from 'cps/';
export default {
    ListData,
    FormData,
    DialogInfo,
    EchartsBarDefault:Echarts.Bar.Default,
	EchartsBarHorizontal:Echarts.Bar.Horizontal,
	EchartsLineDefault:Echarts.Line.Default,
	EchartsPieDefault:Echarts.Pie.Default
};
```

> - 注意:导出的key必须是大写驼峰，注册之后，就变成了小写中横线。
> - 之所以弄一个中转站，是因为，有的组件可能未必会用到，只是备用，没必要注册，所以通过中转站，把常用的需要注册为全局的，在中转站暴露出去，然后在进行全局注册。
> - 其他的注册同一个道理。