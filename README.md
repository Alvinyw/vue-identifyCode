# Identifycode
基于 Vue 的生成图形校验码组件

## 一、通过 Node 引用

```javascript
npm i vue-identifycode
```

在 VUE 的 SPA 中的使用示例：

```html
<template>
  <div id="main">
    <div class="item">
      <input :value="identifyCode" />
      <span class="code" @click="refreshCode">
        <IdentifyCode :identify-code="identifyCode" :content-width="100" :content-height="48"></IdentifyCode>
      </span>
    </div>
  </div>
</template>
<script>
import IdentifyCode from "vue-identifycode"; // 引入包

export default {
  name: "IdentifyCodeTest",
  components: { IdentifyCode },
  data() {
    return {
      identifyCode: ""
    };
  },
  mounted() {
    this.identifyCode = this.createCode();
  },
  methods: {
    createCode() {
      let code = "";
      const codeLength = 4; // 验证码的长度
      // eslint-disable-next-line no-array-constructor
      const random = new Array(2,3,4,5,6,7,8,9,"A","B","C", "D","E","F","G",
        "H","J","K","L","M","N","P","Q","R","S","T","U","V","W","X","Y","Z"
      ); // 随机数
      for (let i = 0; i < codeLength; i++) {
        // 循环操作
        const index = Math.floor(Math.random() * 32); // 取得随机数的索引（0~35）
        code += random[index]; // 根据索引取得随机数加到code上
      }
      return code;
    },
    refreshCode() {
      this.identifyCode = this.createCode();
    }
  }
};
</script>
<style lang="scss" scoped>
#main {
  padding: 15px;
  .item {
    position: relative;
    input {
      width: 100%;
      height: 50px;
      padding: 0 100px 0 6px;
      border-radius: 2px;
      outline: none;
      border: 1px solid #444;
      font-size: 20px;
    }
    .code {
      position: absolute;
      right: 1px;
      top: 1px;
      display: inline-block;
    }
  }
}
</style>
```

## 二、示例

[Demo](https://alvinyw.github.io/Blog/mobile-demo/#/identifyCode)