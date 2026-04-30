---
title: element-ui单选
date: 2026-04-29 17:53:02
tags:
---
1. css隐藏表头全选
``` css
::v-deep thead {
  .el-checkbox {
    display: none;
  }
}
```
2. 增加单选判断
这里踩了个小坑 handleSelectionChange 要写在select方法中 不能写在select-change中 否则clearSelection会触发select-change 造成死循环
``` html
<el-table ref="multipleTable" :data="dialogTableData" :header-cell-style="{ 'background-color': '#e5edfd', color: '#000' }" size='mini' style="width: 100%" @select="handleSelectionChange" @row-click="cellClick">
```

``` javascript
handleSelectionChange(selection, row) {
  this.$refs.multipleTable.clearSelection();
  this.$refs.multipleTable.toggleRowSelection(row);
  this.multipleSelection = [row];
}
```