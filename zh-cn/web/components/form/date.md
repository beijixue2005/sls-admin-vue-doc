# 日期组件

| 属性 |说明    |    类型   |  必填   |    可选值    |  默认值 |
| --- | --- | --- | --- | ---- | ---- |
| key        |      字段名称   |  String   |    Y  |    -   |   -    |
| type        |      字段类型   |  String   |    N  |    input   |   input    |
| label        |     label文本   |  String   |    N  |    date/daterange/year/month/week   |   -    |
| desc        |     占位符   |  String   |    N  |    -   |   -    |
| date_attrs        |      ElementUI支持的属性，看下文   |  Object   |    N  |    -   |   {}    |
| events        |      ElementUI支持的事件，看下文   |  Object   |    N  |    -   |   {}    |


### list数组中每个元素是一个对象，包含如下属性
|属性        |      说明    |    类型   |         必填     |    可选值    |        默认值 |
| --- | --- | --- | --- |----|----|
| text        |      显示的文本   |  String   |  Y    |    -   |   -    |
| value        |      需要获取的value值   |  String   |    Y  |    -   |   -    |


### date_attrs和options_attr和events参考input组件中的说明。

### 特殊说明
#### events事件中的change返回参数说明 **(当type值为daterange时可用，其他都和官方一样)**
>此事件返回参数，我做了处理，统一返回一个对象，对象属性如下

|属性        |      说明    |    类型   |
| --- | --- | --- |
| value        |      字符串值，格式为  "开始时间 分隔符 结束时间"   |  String   |
| info        |      数组值，两个元素，第一个元素为开始时间，第二个元素为结束时间   |  Array   |


