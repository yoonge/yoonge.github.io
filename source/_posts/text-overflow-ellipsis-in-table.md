title: 在表格中使用 text-overflow ellipsis
date: 2014-04-03 10:53:17
tags:
    - table
    - text-overflow
    - ellipsis
categories: Front-End
---
看过很多在 table 中使用 text-overflow: ellipsis 效果的，都是在表格内容上套一层 div 来实现，其实不用那么麻烦，只需为 table 增加一个 table-layout: fixed 样式就可以了。

``` css
table {
    table-layout: fixed;
}
td {
    width: 30%;    /* 可以是固定宽度，也可以是百分比 */
    text-overflow: ellipsis;    /* 也可以是 clip */
    white-space: nowrap;    /* 强制不换行 */
    overflow: hidden;    /* text-overflow 生效的必要条件 */
}
```

## 关于 table-layout 属性

<!--more-->

### 定义和用法

table-layout 属性用来定义表格单元格、行、列的算法规则。

### 自动表格布局：automatic （默认）

在自动表格布局中，列的宽度是由列单元格中没有折行的最宽的内容设定的。
此算法有时会较慢，这是由于它需要在确定最终的布局之前访问表格中所有的内容。

### 固定表格布局：fixed

固定表格布局与自动表格布局相比，允许浏览器更快地对表格进行布局。
在固定表格布局中，水平布局仅取决于表格宽度、列宽度、表格边框宽度、单元格间距，而与单元格的内容无关。
通过使用固定表格布局，用户代理在接收到第一行后就可以显示表格。
