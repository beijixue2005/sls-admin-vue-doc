# checkbox
|属性        |      说明    |    类型   |         必填     |    可选值    |        默认值 |
| --- | --- | --- | --- |----|----|
| key        |      字段名称   |  String   |    Y  |    -   |   -    |
| type        |      字段列表   |  String   |    N  |    input   |   input    |
| label        |      label文本   |  String   |    N  |    -   |   -    |
| list        |      下拉选项，看下文   |  Array   |    Y  |    -   |   []    |
| checkbox_group_attrs        |      ElementUI支持的属性，看下文   |  Object   |    N  |    -   |   {}    |
| checkbox_attrs        |      ElementUI支持的属性，看下文   |  Object   |    N  |    -   |   {}    |
| events        |      ElementUI支持的事件，看下文   |  Object   |    N  |    -   |   {}    |

### list数组中每个元素是一个对象，包含如下属性
|属性        |      说明    |    类型   |         必填     |    可选值    |        默认值 |
| --- | --- | --- | --- |----|----|
| text        |      显示的文本   |  String   |  Y    |    -   |   -    |
| value        |      需要获取的value值   |  String   |    Y  |    -   |   -    |

### checkbox_group_attrs和checkbox_attrs和events参考input组件中的说明。

### 特殊说明
#### events事件中的change返回参数说明
>此事件返回参数，我做了处理，统一返回一个对象，对象属性如下

|属性        |      说明    |    类型   |
| --- | --- | --- | --- |----|----|
| value        |      选中的值   |  Array   |
| info        |      选中的值对应的文本，和value一一对应   |  Array   |


