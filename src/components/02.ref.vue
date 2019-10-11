<template>
  <div>
    <p>count的值为 {{refCount}}</p>
    <button @click="refCount+=1">+1</button>
  </div>
</template>

<script>
import { ref } from "@vue/composition-api";

export default {
  setup() {
    const refCount = ref(0);
    console.log(refCount.value);

    return {
      refCount
    };
  }
};
</script>