# editor
> 目前只支持wangeditor富文本编辑器

使用前先安装最新版本wangeditor，当前最新版本为3.xxx

### [wangEditor官方文档](http://www.wangeditor.com/)，一定要先看下官方文档再使用这个。

|属性        |      说明    |    类型   |         必填     |    可选值    |        默认值 |
| --- | --- | --- | --- |----|----|
| id        |      dom的ID属性，不填内部会生成唯一的ID   |  String   |    N  |    -   |   -    |
| key        |      字段名称   |  String   |    Y  |    -   |   -    |
| type        |      字段列表   |  String   |    N  |    editor   |   -    |
| label        |      label文本   |  String   |    N  |    -   |   -    |
| desc        |      占位符   |  String   |    N  |    -   |   -    |
| config        |     编辑器配置参数   |  Object   |    N  |    -   |   {}    |

### config对象默认值如下
```js
{
    hide_menus:[],//需要隐藏的菜单
    show_menus:[],//需要显示的菜单
    //上面两个都存在时，将会取show_menus，而忽略hide_menus
    
    attrs:{
        zIndex: 100,//富文本层级
        
        uploadImgShowBase64: false,   // 使用 base64 保存图片
        uploadImgServer    : '',// 上传图片到服务器
        //官方建议上面两个二选一。
        
        showLinkImg        : true,//隐藏“网络图片”tab
        uploadImgMaxSize   : 5 * 1024 * 1024,//默认限制图片大小是 5M
        uploadImgMaxLength : 10000,//限制一次最多能传几张图片,默认为 10000 张（即不限制），需要限制可自己配置
        uploadImgParams    : {},//上传图片时可自定义传递一些参数，例如传递验证的token等。这些参数会拼接到 url 的参数中，也会被添加到formdata中。
        uploadFileName     : '',//上传图片时，可自定义filename，即在使用formdata.append(name, file)添加图片文件时，自定义第一个参数。
        uploadImgHeaders   : {},//上传图片时刻自定义设置 header
        withCredentials    : false,//跨域上传中如果需要传递 cookie 需设置 withCredentials
        uploadImgTimeout   : 5000,//默认的 timeout 时间是 5 秒钟
    },
    events:{
        //before: function (xhr, editor, files) {},
        //success: function (xhr, editor, result) {},
        //fail: function (xhr, editor, result) {},
        //error: function (xhr, editor) {},
        //timeout: function (xhr, editor) {},
       // customInsert: function (insertImg, result, editor) {}
    }
}
```


