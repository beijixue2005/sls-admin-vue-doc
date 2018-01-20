# input
|属性        |      说明    |    类型   |         必填     |    可选值    |        默认值 |
| --- | --- | --- | --- |----|----|
| key        |      字段名称   |  String   |    Y  |    -   |   -    |
| type        |      字段列表   |  String   |    N  |    input   |   input    |
| label        |      label文本   |  String   |    N  |    -   |   -    |
| desc        |      占位符   |  String   |    N  |    -   |   -    |
| attrs        |      ElementUI支持的属性，看下文   |  Object   |    N  |    -   |   {}    |
| events        |      ElementUI支持的事件，看下文   |  Object   |    N  |    -   |   {}    |

### attrs对象格式如下:
 ElementUI的Input Attributes中支持什么，都可以填到这里面
```js
{
   maxlength:10,
   minlength:3,
   ......
}
```

### events对象格式如下:
 ElementUI的Input Events中支持什么，都可以填到这里面
```js
{
    click:()=>{},
    blur:()=>{},
    focus:()=>{},
    change:()=>{}      
    ,,,,,,    
}
```


