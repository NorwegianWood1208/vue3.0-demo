<template>
  <div>

  </div>
</template>

<script>
import { watch, ref, reactive } from "@vue/composition-api";

export default {
  setup() {
    // const refCount = ref(0);

    // watch(() => console.log(refCount.value));

    // setTimeout(() => {
    //   refCount.value += 1;
    // }, 1500);

    // ------------------------------

    // const state = reactive({
    //   count: 0
    // });

    // watch(
    //   () => state.count,
    //   (newVal, oldVal) => {
    //     console.log(newVal, oldVal);
    //   },
    //   {
    //     lazy: true
    //   }
    // );

    // setTimeout(() => {
    //   state.count += 1;
    // }, 1500);

    // ---------------------------

    const state = reactive({
      count: 0,
      name: "zs"
    });

    watch(
      [() => state.count, () => state.name],
      ([newCount, newName], [oldCount, oldName]) => {
        console.log(newCount, newName);
        console.log(oldCount, oldName);
      },
      {
        lazy: true
      }
    );

    setTimeout(() => {
      state.count += 1;
    }, 1500);

    setTimeout(() => {
      state.name += "彬哥";
    }, 3000);
  }
};
</script>