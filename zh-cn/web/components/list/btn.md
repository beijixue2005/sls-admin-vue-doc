# 按钮

- 默认显示五个按钮，表格上面有个添加按钮和批量删除按钮
- 列表最后的操作默认显示3个按钮(查看，修改，删除)

### 可通过以下方式自定义按钮
```html
<list-data
                :BtnInfo="btn_info"></list-data>
```
```js
btn_info:{
    width:300,//按钮操作列的宽度

    // all:false,//false:不显示按钮操作列
    // default:false,//false:不显示默认所有按钮(查看，修改，删除)，但是显示列
    // select:false,//false:不显示查看按钮
    select_text:'查看',//查看文本，默认只有图标
	// update:false,//false:不显示修改按钮
	update_text:'修改',//修改文本，默认只有图标
	// delete:false,//false:不显示删除按钮
	delete_text:'删除',//删除文本，默认只有图标
	// add:false,//false：不显示添加按钮
	add_text:'添加功能',//添加文本，默认只有图标
	
	// batch:false,//false:不显示批量选择功能，同时内置批量删除按钮也不显示
	// batch_delete:false,//false:不显示批量删除按钮
	batch_delete_text:'批量删除功能',//批量删除文本，默认删除选中
	
    //增加自定义按钮，默认会排到默认按钮的右边
    list:[{
        text:'同步',//按钮文本
        type:'warning',//按钮类型，遵循elementUI的几种按钮类型
        //如果不传fn回调，默认会触发onClickBtn方法，传了则只触发fn。
        fn:(opts)=>{
            console.log('custom btn cb');
            console.log(opts);
        }
    },{
		text:'刷新',
        type:'primary'
	}],
	
    // list_position:'before'//默认不传或者为after在默认按钮的后边,before则在前边。
},
```

### 按钮内置支持以下事件
|事件名        |      说明    | 
| --- | --- | --- | --- |----|----|
| onClickBtn        |      当自定义了按钮，并且没有自定义fn回调时触发   | 
| onClickBtnAdd        |      添加按钮事件   | 
| onClickBtnSelect        |      查看按钮事件   | 
| onClickBtnUpdate        |      修改按钮事件   | 
| onClickBtnDelete        |      删除按钮事件   | 
| onClickBtnBatchDelete        |      批量删除按钮事件   | 
| onSelectionChange        |      批量选择，改变CheckBox状态事件   | 
|   onSearch    |      点击搜索事件      |

#### 以上事件出onSearch之外，不管是内置按钮事件还是自定义按钮的回调事件，均返回一个对象，包含如下属性(根据按钮类型，包含不同属性):

|属性名        |      说明    |   类型    |   可选值   |
| --- | --- | --- | --- |----|----|
| type        |      按钮类型   |   String   |  Add/Select/Update/Delete/BatchDelete(批量删除)    |
| list        |      列表数据 数组  |   Array  |  [] |
| data        |      当前行数据对象   |   Object | {} |
| dataIndex        |      当前行索引   |   Number | - |
| btnIndex        |      当前按钮索引，自定义按钮才有此属性   | Number | - | 
| btnInfo       |      当前按钮对象，自定义按钮才有此属性   |    Object | {} |
| ids       |     选中的数组，从下面的datas提取出的id    |    Array | {} |
| datas       |      选中的数据，包含每个选中的元素对象   |    Array | {} |

> 注意:上面ids和datas只有onSelectionChange和onClickBtnBatchDelete两个事件触发。

### slot
|具名        |      说明    | 
| --- | --- | 
| header-before        |      在批量按钮和添加按钮的前面添加自定义内容   | 
| header-after        |      在批量按钮和添加按钮的后面添加自定义内容  |