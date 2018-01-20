# 折叠功能

```html
<list-data
    :List='list'
    :Expand="expand"
    :FieldList='fields'>
    <template
            scope="props"
            slot="expand">
        <div>索引：{{props.index}}</div>
        <div>地址：{{props.data.address}}</div>
        <div>行数据：{{JSON.stringify(props.data)}}</div>
    </template>
</list-data>
```
```js
export default {
    data() {
        return {
            list: [],
            fields: [{
                key: 'name',
                label: '标题'
            }],
            expand:{
                show:true,
                position:'right'
            }
        }
    },
    created(){
        for(let i=1;i<=3;i++){
            this.list.push({
                name:'赛冷思'+i,
                address:'北京上海第 '+i+" 区",
            });
        }
    },
}
```

### Expand属性是一个对象，包含如下属性
|属性        |      说明    |    类型   |         必填     |    可选值    |        默认值 |
| --- | --- | --- | --- |----|----|
| show        |      是否显示折叠   |  Boolean   |    Y  |    true/false   |   false    |
| position        |      折叠按钮位置   |  String   |    N  |    left/right   |   left    |

### Expand的slot='expand',scope返回一个对象，包含如下属性
|属性        |      说明    |    类型   | 
| --- | --- | --- | --- |----|----|
| index        |      当前行的索引   |  Number   | 
| data        |      当前行数据对象   |  Object   | 

