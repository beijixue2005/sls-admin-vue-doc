# radio
|属性        |      说明    |    类型   |         必填     |    可选值    |        默认值 |
| --- | --- | --- | --- |----|----|
| key        |      字段名称   |  String   |    Y  |    -   |   -    |
| type        |      字段类型   |  String   |    Y  |    radio   |   -    |
| label        |      radio的label   |  String   |    N  |    -   |   -    |
| list        |      选项列表，看下文   |  Array   |    Y  |    -   |   []    |
| radio_attrs        |      ElementUI支持的属性，看下文   |  Object   |    N  |    -   |   {}    |
| events        |      ElementUI支持的事件，看下文   |  Object   |    N  |    -   |   {}    |

### list数组中每个元素是一个对象，包含如下属性
|属性        |      说明    |    类型   |         必填     |    可选值    |        默认值 |
| --- | --- | --- | --- |----|----|
| text        |      显示的文本   |  String   |  Y    |    -   |   -    |
| value        |      需要获取的value值   |  String   |    Y  |    -   |   -    |

### radio_attrs和events参考input组件中的说明。

### 特殊说明
#### events事件中的change返回参数说明
>官方文档，单选只返回value值，多选则返回一个value数组，我做了处理，统一返回一个对象，对象属性如下

|属性        |      说明    |    类型   |
| --- | --- | --- | --- |----|----|
| value        |      选中的值   |  String，Number  |
| info        |      选中的值对应的文本   |  String，Number   |


