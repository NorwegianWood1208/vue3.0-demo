<template>
  <div>
    <!-- <com-setup p1="aaaaaaa" /> -->
    <!-- <com-ref /> -->
    <!-- <com-torefs /> -->
    <!-- <com-computed /> -->
    <!-- <com-watch1 /> -->
    <!-- <com-watch2 /> -->
    <!-- <com-watch3 /> -->

    <com-nexttick />

    <hr />

    <com-refdom />

    <p>--------------------------------</p>

    <h1>父组件</h1>

    <button @click="showCom">打印 comRef 的值</button>
    <br />
    <button @click="color='red'">红色</button>
    <button @click="color='yellow'">黄色</button>
    <button @click="color='blue'">蓝色</button>

    <hr>

    <com-son ref="comRef" />

  </div>
</template>

<script>
import SetUpCom from "./components/01.setup";
import ComRef from "./components/02.ref";
import ComToRefs from "./components/03.toRefs";
import ComComputed from "./components/04.computed";
import ComWatch1 from "./components/05.watch-01";
import ComWatch2 from "./components/06.watch-02";
import ComWatch3 from "./components/07.watch-03";
import ComSon from "./components/08.son";
import ComRefDOM from "./components/10.refDOM";
import ComNextTick from "./components/11.nextTick";

import { provide, ref } from "@vue/composition-api";

export default {
  name: "app",
  components: {
    "com-setup": SetUpCom,
    "com-ref": ComRef,
    "com-torefs": ComToRefs,
    "com-computed": ComComputed,
    "com-watch1": ComWatch1,
    "com-watch2": ComWatch2,
    "com-watch3": ComWatch3,
    "com-son": ComSon,
    "com-refdom": ComRefDOM,
    "com-nexttick": ComNextTick
  },
  setup() {
    const color = ref("red");
    provide("themeColor", color);

    const comRef = ref(null);

    const refCountApp = ref(0);

    const updateCountBySon = val => {
      refCountApp.value = val;
    };

    const showCom = () => {
      console.log(comRef);
      console.log("str1的值是    " + comRef.value.str1);
      comRef.value.setStr();
    };

    return {
      color,
      comRef,
      showCom
    };
  }
};
</script>

<style>
</style>
