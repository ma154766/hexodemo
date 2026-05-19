---
title: vue祖孙插槽使用
date: 2026-05-19 15:09:00
tags:
---

1. 祖先组件代码

```html
<DialogForm
  @submit="submitDialogFormFuc"
  :title="dialogFormTitle"
  dialogWidth="700px"
  labelWidth="200px"
  :formData="dialogFormData"
  :config="dialogConfig"
  :visible.sync="dialogFormVisible"
>
  <template v-slot:form-targetIpDirectType> 1231313 </template>
</DialogForm>
```

2. 父组件

```html
<CommonForm
  @submitForm="submit"
  @cancel="cancel"
  :footerBtn="footerBtn"
  :that="that"
  :labelWidth="labelWidth"
  :formData="formData"
  :config="config"
>
  //这样就可以穿透到孙组件
  <template v-for="(slotFn, name) in $scopedSlots" v-slot:[name]="slotProps">
    <slot :name="name" v-bind="slotProps"></slot>
  </template>
</CommonForm>
```
