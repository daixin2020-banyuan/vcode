<template>
  <div class="login">
    <h1>请输入手机号</h1>
    <input
      placeholder="请输入手机号"
      class="input"
      v-model="inputValue"
      maxlength="11"
      @keyup="control"
    />
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Login",
  data() {
    return {
      inputValue: ""
    };
  },
  methods: {
    control() {
      const reg = /^\d*?$/;
      if (reg.test(this.inputValue)) {
        if (this.inputValue.length === 11) {
          this.$router.push({
            name: "Vcode"
          });
        }
      } else {
        this.$notify.error({
          title: "错误",
          message: "请输入数字"
        });
      }
    }
  }
};
</script>

<style lang="scss">
.input {
  width: 400px;
  text-align: center;
  border: none;
  border-bottom: 1px solid black;
  outline: none;
}
h1 {
  margin: 0 auto;
  text-align: center;
}
</style>
