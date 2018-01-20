# 搜索

```html
<list-data
        :Search="search_data"
        @onSearch="onSearch"></list-data>
```
```js
search_data:{
	fields: [{
		key  : 'cate',
		type : 'select',
		multiple: false,
		list   : [{
			value: 'jishu',
			text : '技术'
		}, {
			value: 'sanwen',
			text : '散文'
		}, {
			value: 'qita',
			text : '其他'
		}],
		desc : '请选择分类',
		label: ''
	}, {
		label: '',
		key: 'input',
		desc: '请输入标题'
	}],
}
```
> - 传入Search属性。
> - onSearch点击搜索按钮事件。

### Search属性
|属性        |      说明    |    类型   |         必填     |    可选值    |        默认值 |
| --- | --- | --- | --- |----|----|
| fields        |      就是表单自带列表,参考表单   |  Array   |    Y  |    -   |   []    |

### onSearch事件
> 就是表单组件传提交事件，参考表单组件。