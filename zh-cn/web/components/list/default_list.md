# 默认列表
>默认情况只需要传List和FieldList即可渲染。

例如下面是一个简单的渲染列表例子
```html
<list-data
            :List='list'
            :FieldList='fields'></list-data>
```
```js
list: [{
    id:1,
    name:'赛',
},{
    id:2,
    name:'冷',
},{
    id:3,
    name:'思',
}],
fields: [{
	key: 'id',
	label: 'ID'
},{
    key: 'name',
    label: '姓名'
}]
```

> - list就是正常的列表数据
> - fields就是字段列表，默认情况只需要key和label。key:字段名；label:就是表格的表头