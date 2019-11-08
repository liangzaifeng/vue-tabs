#Tabs使用说明
---



```vue
<template>
  <div>
     <!-- 默认配置 -->
    <Tabs v-model="active" :list="list" @click="handleClick" />
    <!-- 使用自定义配置 -->
    <Tabs v-model="activeName" :list="tabList" @click="handleClick" :props="props" />
  </div>
</template>

import Tabs from "@/components/Tabs";
export default {
  name: "register",
  components: { Tabs },
  data() {
    return {
      // 默认配置
      active: 1,
      list: [
        { id: 1, label: "tabs1" },
        { id: 2, label: "tabs2" }
      ],
      
      // 自定义配置
      activeName: 1,
      tabList: [
        { number: 1, text: "tabs1" },
        { number: 2, text: "tabs2" }
      ],
      props:{
        label: 'text',
        id: 'number'
      }
    };
  },
  methods: {
    handleClick(item){
      console.log(item);
    }
  },
};

```

###Attributes
---
| 参数    | 说明               | 类型            | 可选择 | 默认值 |
| ------- | ------------------ | --------------- | ------ | ------ |
| v-model | 绑定值, 默认选中项 | string / number | —      | —      |
| list | 渲染的数组 | array | —      | —      |
| active-color | 默认选中项的颜色 | string | —      | blue      |
| color | 文本颜色 | string | —      | `#444`     |
| height | 行高 | string / number | —      | —      |
| props | 配置选项，具体看下表 | object | —      | —      |



###props
---
| 参数 | 说明 | 类型 | 可选择 | 默认值 |
| ---- | ---- | ---- | ------ | ------ |
| label | 指定为展示在页面的值 | string | —    | label |
| id   | 绑定值, 默认选中项 | string / number | —    | id   |



### Events:
---
| 参数 | 说明 | 回调参数 |
| ---- | ---- | ---- |
| click | 点击事件 | item(选中的当前对象) |





