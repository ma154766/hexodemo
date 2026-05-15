---
title: el-table 双击展开行单元格 导致展开行关闭
date: 2026-05-15 15:03:58
tags:
---

1.

```html
<div
  title="双击编辑"
  @dblclick="showSelect(scope.row, 'isclkTypeEdit')"
  v-if="!scope.row.isclkTypeEdit"
>
  {{ scope.row.clkType ? clickTypelist[scope.row.clkType] : "无" }}
</div>
```

2. 解决办法：增加 row-key

```html
<el-table
  :data="tableData"
  style="width: 100%"
  row-key="Id"
  border
  :header-cell-style="{ 'background-color': '#e5edfd', color: '#000' }"
  v-loading="loading"
></el-table>
```
