<template>
  <div>
    <h1>学习 $nextTick</h1>

    <button v-if="isShowInput === false" @click="showInput">展示文本框</button>
    <input type="text" v-else ref="ipt">
  </div>
</template>

<script>
export default {
  data() {
    return {
      isShowInput: false
    };
  },
  methods: {
    showInput() {
      this.isShowInput = true;
      // this.$refs.ipt.focus();

      // 当组件根据最新的 data 数据，重新渲染完成之后，再执行回调函数中的操作
      this.$nextTick(() => {
        this.$refs.ipt.focus();
      });
    }
  }
};
</script>