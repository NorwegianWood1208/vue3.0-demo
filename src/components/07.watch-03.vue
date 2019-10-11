<template>
  <div>
    <input type="text" v-model="kw">
  </div>
</template>

<script>
import { ref, watch, onBeforeMount, onMounted } from "@vue/composition-api";

export default {
  setup() {
    const kw = ref("");

    // 专门负责打印的函数
    const asyncPrint = val => {
      return setTimeout(() => {
        console.log(val);
      }, 1000);
    };

    watch(
      kw,
      (newVal, oldVal, clean) => {
        const timerId = asyncPrint(newVal);

        // 清除之前未完成的异步任务
        clean(() => clearTimeout(timerId));
      },
      { lazy: true }
    );

    onBeforeMount(() => {
      console.log("onBeforeMount");
    });

    onMounted(() => {
      console.log("onMounted");
    });

    return {
      kw
    };
  }
};
</script>