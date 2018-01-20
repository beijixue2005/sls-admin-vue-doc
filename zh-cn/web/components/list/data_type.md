# 数据类型

> 有时候可能并不是直接显示字段的值，比如链接或者图片，这里也提供了设置的地方。

```js
list: [{
    id:1,
    name:'赛',
    image:'https://sailengsi.com/Public/home/2016/images/logo.png',
    url:'https://sailengsi.com',
	github:'https://github.com',
	slsadmin:'https://github.com/sailengsi/sls-admin',
},{
    id:2,
    name:'冷',
	image:'https://sailengsi.com/Public/home/2016/images/logo.png',
	url:'https://sailengsi.com',
	github:'https://github.com',
	slsadmin:'https://github.com/sailengsi/sls-admin',
},{
    id:3,
    name:'思',
	image:'https://sailengsi.com/Public/home/2016/images/logo.png',
	url:'https://sailengsi.com',
	github:'https://github.com',
	slsadmin:'https://github.com/sailengsi/sls-admin',
}],
fields: [{
    type:'image',
    key: 'image',
    label: '图片',
	host:'',
	width:'100',
	height:'100'
},{
    key: 'name',
    label: '姓名'
},{
	key: 'url',
	label: '网址(链接)',
	type:'link',
	link_text:'官方网址(新开窗口打开)',
	link_target:'_blank'
},{
	key: 'github',
	label: 'Github(链接)',
	type:'link',
	link_text:'github(当前窗口打开)',
},{
	key: 'slsadmin',
	label: 'slsadmin(默认显示连接)',
	type:'link',
}]
```

> - 如果是图片，fields中设置type为image。组件内部就会当图片处理，有时候后台返回的仅仅是一个路径，并且图片所在域名和我们前端域名不同，这时候可以把域名设置到host属性，组件内部检测到host有值时会自动拼接。
> - 如果是图片，fields中设置type为link。如果只设置link，默认显示文本为连接地址，打开方式为当前窗口；如果设置link_text,则会成显示文本；如果设置link_target，则会当成打开连接的方式。