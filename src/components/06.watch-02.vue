<template>
  <div>
    <p>count {{refCount}}</p>
    <button @click="stopWatch">停止监视</button>
  </div>
</template>

<script>
import { ref, watch } from "@vue/composition-api";

export default {
  setup() {
    const refCount = ref(0);

    const stop = watch(() => {
      console.log("监听到了 refCount 的变化");
      console.log(refCount.value);
    });

    // 停止监视
    const stopWatch = () => {
      stop();
    };

    setTimeout(() => {
      refCount.value += 1;
    }, 3000);

    return {
      refCount,
      stopWatch
    };
  }
};
</script>