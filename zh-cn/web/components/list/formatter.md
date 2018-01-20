# 格式化

```js
types:{
    'A':'顶级',
    'B':'一级',
    'C':'二级',
    'D':'三级'
},
list: [{
    id:1,
    name:'赛',
    type:'A',
    status:1
},{
    id:2,
    name:'冷',
    type:'B',
    status:2
},{
    id:3,
    name:'思',
    type:'C',
    status:1
}],
fields: [{
    key: 'name',
    label: '姓名'
}, {
    key: 'type',
    label: '级别',
    formatter: (item)=> {
        return this.types[item.type];
    }
},  {
    key: 'status',
    label: '状态',
    formatter: (item)=> {
        return item.status == 1 ? '启用' : '禁用';
    }
}]
```

> fields中加入formatter回调函数，参考官方文档即可。