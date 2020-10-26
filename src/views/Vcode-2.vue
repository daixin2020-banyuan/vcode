<template>
  <div class="vcode">
    <h1>请输入验证码</h1>

    <div class="input-container">
      <input type="text" v-model="val1" />
      <input type="text" v-model="val2" />
      <input type="text" v-model="val3" />
      <input type="text" v-model="val4" />
    </div>

    <div>
      <input
        type="text"
        v-model="value"
        maxlength="4"
        ref="inputHidden"
        @blur="inputBlur"
        class="input-hidden"
        @keyup="control"
      />
    </div>
  </div>
</template>
<script>
export default {
  name: "Vcode",
  data() {
    return {
      value: ""
    };
  },
  mounted() {
    this.focusInput();
  },
  computed: {
    val1: function() {
      return this.value.charAt(0);
    },
    val2: function() {
      return this.value.charAt(1);
    },
    val3: function() {
      return this.value.charAt(2);
    },
    val4: function() {
      return this.value.charAt(3);
    }
  },
  methods: {
    focusInput() {
      this.$refs.inputHidden.focus();
    },
    inputBlur() {
      this.focusInput();
      // this.$refs.inputHidden.focus();
    },
    control() {
      const reg = /^\d*?$/;
      if (reg.test(this.value)) {
        if (this.value.length === 4) {
          console.log("验证码1====", this.val1);
          console.log("验证码2====", this.val2);
          console.log("验证码3====", this.val3);
          console.log("验证码4====", this.val4);
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
.input-container {
  display: flex;
  flex-direction: row;
  width: 500px;
  margin: 0 auto;
  input {
    width: 100px;
    margin-right: 20px;
    text-align: center;
    border: none;
    border-bottom: 1px solid black;
    outline: none;
  }
}
h1 {
  margin: 0 auto;
  text-align: center;
}

input:disabled {
  background-color: white;
}
.input-hidden {
  color: rgba($color: #ffffff, $alpha: 0);
  border: none;
  outline: none;
}
</style>
