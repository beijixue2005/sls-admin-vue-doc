# switch
|属性        |      说明    |    类型   |         必填     |    可选值    |        默认值 |
| --- | --- | --- | --- |----|----|
| key        |      字段名称   |  String   |    Y  |    -   |   -    |
| type        |      控件类型   |  String   |    Y  |    radio   |   -    |
| label        |      label文本   |  String   |    N  |    -   |   -    |
| value        |      开关选项，看下文   |  Object   |    Y  |    -   |   []    |
| switch_attrs        |      ElementUI支持的属性，看下文   |  Object   |    N  |    -   |   {}    |
| events        |      ElementUI支持的事件，看下文   |  Object   |    N  |    -   |   {}    |

### value是一个对象，包含如下属性
|属性        |      说明    |    类型   |         必填     |    可选值    |        默认值 |
| --- | --- | --- | --- |----|----|
| on        |      开的文本   |  String   |  Y    |    -   |   -    |
| off        |      关的文本   |  String   |    Y  |    -   |   -    |

### switch_attrs和events参考input组件中的说明。

### 特殊说明
#### events事件中的change返回参数说明
>此事件返回参数，我做了处理，统一返回一个对象，对象属性如下

|属性        |      说明    |    类型   |
| --- | --- | --- | --- |----|----|
| value        |      反正的状态，布尔值true/false   |  Boolean  |
| info        |      状态值对应的文本，值为true返回value中on的值，反之则是off的值   |  String   |



