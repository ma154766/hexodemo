---
title: pagesize * current 大于total问题的解决
date: 2026-04-17 10:28:25
tags:
---
1. element-plus组件如果pagesize * current 大于total 则会重新计算并运行onCurrentChange和onSizeChange 两个请求一起发出 有可能onSizeChange返回的慢 数据为空被重新覆盖掉
![''](/img/2026/04/17/image.png)

1. 对onSizeChange进行判断
``` js
  const onSizeChange = val => {
    if (
      tableData.value.pagination.currentPage * val >
      tableData.value.pagination.total && tableData.value.pagination.currentPage !== 1
    ) {
      // 比总数大的时候不走查询 只走分页查询
      return;
    } else {
      handleSearch();
    }
  };

  const onCurrentChange = val => {
    handleSearch();
  };

```
3. 解决效果
![''](/img/2026/04/17/image2.png)
