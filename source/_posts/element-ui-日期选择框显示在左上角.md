---
title: element-ui 日期选择框显示在左上角
date: 2026-05-08 13:40:30
tags:
---
1. bug显示如下
![''](/img/2026/05/08/image.png)

2. 解决办法
加上key值即可
``` html
          <el-date-picker
            v-model="formInline[formItem.prop]"
            type="daterange"
            align="right"
            unlink-panels
            key="date-range"
            :editable="false"
            value-format="yyyy-MM-dd"
            range-separator="至"
            start-placeholder="开始日期"
            end-placeholder="结束日期"
            :picker-options="pickerOptions1"
          >
          </el-date-picker>
```
