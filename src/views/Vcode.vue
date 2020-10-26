<template>
  <div class="vcode">
    <h1>请输入验证码</h1>
    <div class="input-container">
      <div v-for="(item, index) in inputList" :key="index">
        <input
          type="text"
          v-model="item.val"
          class="border-input"
          @keyup="nextFocus($event, index)"
          @keyup.8="prevFocus($event, index)"
          maxlength="1"
          ref="input"
        />
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Vcode",
  data() {
    return {
      inputList: [{ val: "" }, { val: "" }, { val: "" }, { val: "" }]
    };
  },
  methods: {
    nextFocus($event, index) {
      if (this.inputList[index].val !== "" && index <= 2) {
        this.$refs.input[index].disabled = true;
        this.$refs.input[index + 1].focus();
        // this.inputList[index + 1].val = $event.key;
      }
    },
    prevFocus($event, index) {
      // console.log("prevFocus====>", $event);
      // console.log("prevFocus====>", index);
      if (index >= 1) {
        this.$refs.input[index - 1].disabled = false;
        this.$refs.input[index - 1].focus();
        this.inputList[index].val = "";
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
}
h1 {
  margin: 0 auto;
  text-align: center;
}
.border-input {
  width: 100px;
  margin-right: 20px;
  text-align: center;
  border: none;
  border-bottom: 1px solid black;
  outline: none;
}
input:disabled {
  background-color: white;
}
</style>
