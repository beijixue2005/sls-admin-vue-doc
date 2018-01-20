# 分页

```html
<list-data
        @onChangeCurrentPage="onChangeCurPage"
        @onChangePageSize="onChangeCurPageSize"
        :Pagination='pagination'></list-data>
```
```js
pagination: {
    current_page: 1,
    total: 30,
    'page-count':0,
    page_size: 12,
    page_sizes: [3, 9, 12, 24],
    layout: "total, sizes, prev, pager, next, jumper"
},
```
> - 传入Pagination属性。
> - onChangeCurrentPage改变当前页码事件。
> - onChangePageSize改变每页显示数量事件。
> - 具体可参考官方文档。