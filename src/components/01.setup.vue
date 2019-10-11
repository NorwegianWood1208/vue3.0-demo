<template>
  <div>
    <p>count值为 {{count}}</p>
    <button @click="count+=1">+1</button>
  </div>
</template>

<script>
import { reactive } from "@vue/composition-api";

export default {
  setup(props, ctx) {
    // console.log("setup");
    // console.log(props);
    // console.log(ctx);

    const state = reactive({ count: 0 });

    // console.log(state);
    // state.count += 1;
    // console.log(state)

    return state;
  },
  beforeCreate() {
    // console.log("beforeCreate");
  },
  created() {
    // console.log("created");
  },
  props: {
    p1: String
  }
};
</script>