# 表单组件
vwebpack2版本，自动被注册为全局组件FormData

在组件中无需引入即可直接使用：
```html
<form-data></form-data>
```


## 属性

|参数        |      说明    |    类型   |         必填     |    可选值    |        默认值 |
| --- | --- | --- | --- |----|----|
| FieldList        |      字段列表，看下文   |  Array   |     Y  |    -   |   []    |
| DefaultValue        |      默认值，看下文   |  Object   |     N  |    -   |   {}    |

### FieldList
此数组为表单控件元素列表，例如，表单中有多少选项，此数组就会有几个元素，例如渲染一个input控件的话，FieldList需要以下格式:
```JavaScript
[
    {
        type:'input',//控件类型
        key:'field_name',//字段的名称
        label:'表单左边的名称',//表单左边显示的label
        desc:'input的placeholder'//输入框占位符
    }
]
```
可以看到，上面只是定义了几个常用属性，我们知道，ElementUI支持很多属性以及事件，那么，在这里需要怎么写呢？下面以input为例，假如要增加其他属性以及事件的写法如下:
```JavaScript
[
    {
        type:'input',//控件类型
        key:'field_name',//字段的名称
        label:'表单左边的名称',//表单左边显示的label
        desc:'input的placeholder',//输入框占位符
        attrs:{
            
        },//在此对象中，可以把ElementUI提供的属性全部放到这里
        events:{
            change:(value)=>{
                console.log(value);
            }
        }
    }
]
```
**注意:上面的attrs属性名，此属性名不是固定的，因为在ElementUI官方文档可以看到，某些控件的属性，是有多种的，比如select控件，有select属性，有option属性，所以，这个属性名，在这里，就没有必要是固定的了。**

事件的属性名events，此值是固定的，任何一个控件，只要ElementUI支持的事件，可以全部写在这个对象里面，需要注意的是，事件中返回的参数，有的是把ElementUI官方的参数原样返回，有的是把值经过了处理之后再返回。例如:我们常用的select，官方只返回value值，那么经过我的处理，不仅返回了值，还返回的对应的文本，也就是select中option绑定的label属性，这个功能我相信是你们最喜欢的。

上面是渲染input的方式，其实关键就是type属性，FormData组件会根据type的不同值，自动渲染对应的表单控件。目前type支持的类型如下。
- input
- textarea
- select
- radio
- switch
- cascader
- checkbox
- date
- daterange
- year
- year
- week
- time
- timerange
- timefixed
- timefixedrange
- datetime
- datetimerange
- editor

上面这所有类型，除了editor之外，所有类型都是ElementUI官方支持。上面只是一个简单的示例，在这一章的下面，会详细的把每一个控件类型作为一节，详细的说明如何使用每一个控件。

### DefaultValue
当需要有默认值得时候，可以写在这个对象中，格式就是key:value。key一定要和FieldList中每个空间的定义的key一致。

## 事件
|事件名        |      说明    |    参数 |   参数类型|
| --- | --- | --- |---|
|   onSubmit  |   提交事件  |   opts    |   Object  |
这是表单提交事件，需要介绍的就是返回的opts参数了。
opts参数是一个对象，其有两个属性，data和info，data是需要提交的数据，格式就是key:value的形式。info则是对应的文本，例如下拉框控件，在data中，字段的值仅仅是值而已，而在info中，则会把对应的文本给返回，方便你做其他处理，详情看demo。


