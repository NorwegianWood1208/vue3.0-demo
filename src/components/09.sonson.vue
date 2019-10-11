<template>
  <div>
    <h5 :style="{color: color}">孙子组件</h5>
  </div>
</template>

<script>
import { inject } from "@vue/composition-api";
export default {
  setup() {
    const color = inject("themeColor");

    return {
      color
    };
  }
};
</script>