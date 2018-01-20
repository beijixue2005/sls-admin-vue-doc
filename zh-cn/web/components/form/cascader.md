# cascader
|属性        |      说明    |    类型   |         必填     |    可选值    |        默认值 |
| --- | --- | --- | --- |----|----|
| key        |      字段名称   |  String   |    Y  |    -   |   -    |
| type        |      字段列表   |  String   |    N  |    input   |   input    |
| label        |      label文本   |  String   |    N  |    -   |   -    |
| desc        |      占位符   |  String   |    N  |    -   |   -    |
| options        |      下拉选项，看下文   |  Array   |    Y  |    -   |   []    |
| cascader_attrs        |      ElementUI支持的属性，看下文   |  Object   |    N  |    -   |   {}    |
| events        |      ElementUI支持的事件，看下文   |  Object   |    N  |    -   |   {}    |

### options数组是一个无线分类结构，具体可参考官方文档或者demo

### cascader_attrs和events参考input组件中的说明。

### 特殊说明
#### events事件中的change和active-item-change返回参数说明
>这两个事件返回参数，我做了处理，统一返回一个对象，对象属性如下

|属性        |      说明    |    类型   |
| --- | --- | --- | --- |----|----|
| value        |      选中的值，数组中元素顺序是从根到选择的最后一级   |  Array   |
| info        |      选中的值对应的文本，和value一一对应   |  Array   |