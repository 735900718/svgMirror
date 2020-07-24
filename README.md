### SVG实现镜像倒影效果

#### 基础用法

##### 效果图：

<img src="https://i.loli.net/2020/07/24/2IqQuXedTROlDbv.png" alt="Snipaste_2020-07-24_09-54-30"  />

##### 代码：

``` vue
<template>
  <div id="app">
    <Mirror :image="logo" :width="200" :height="200" />
  </div>
</template>

<script>
  import Mirror from 'svg-mirror';

  export default {
    name: 'App',
    components: {
      Mirror
    },
    data () {
      return {
        logo: require("./assets/logo.png")
      }
    }
  }
</script>
```

#### 属性

| 参数     | 说明                 | 类型                                     | 可选值 | 默认值                                                       |
| -------- | -------------------- | ---------------------------------------- | ------ | ------------------------------------------------------------ |
| width    | 图片的宽度           | number                                   | —      | 128                                                          |
| Height   | 图片的高度           | number                                   | —      | 128                                                          |
| gap      | 图片与倒影之间的间距 | number                                   | —      | 5                                                            |
| image    | 图片地址             | string                                   | —      | ""                                                           |
| maskStop | 倒影透明设置         | Array<{offset: string, opacity: string}> | —      | [{offset: "0%", opacity: "0"},{offset: "100%", opacity: "1"}] |

> offset: string 类型，可选值"0%" ~ "100%"
>
> opacity: string 类型，可选值"0" ~ "1"