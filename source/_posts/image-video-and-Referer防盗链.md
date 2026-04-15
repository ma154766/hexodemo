---
title: image video and Referer防盗链
date: 2026-04-15 10:17:43
tags:
---

1. 最近在页面接入其他网站video视频资源时 发现直接输入视频地址是好的 如果src引入则报403 
2. 最后发现在request 请求头中 有 referer
![alt text](/img/2026/04/15/image.png)
3. 解决方法 增加标签
```js
<meta name="referrer" content="no-referrer">
```
或者使用

```js
import { useHead } from "@vueuse/head";

useHead({
    meta: [
      {
        name: "referrer",
        content: "no-referrer"
      }
    ]
  });
```


