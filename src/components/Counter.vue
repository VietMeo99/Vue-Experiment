<template>
  <button @click="increment">
    <!-- Count is: {{ state.count }}, double is: {{ state.double }} -->
    <p>count</p>
  </button>
  <!-- <button @click="callback1">
    callback1
  </button> -->
  {{ Math.random() }}
  <br />
  r1: {{ show() }}
  <br />
  r2: {{ show2() }}
  <br />
  <!-- :count="state.count" -->
  <child @some-event="state.count % 2 ? callback1() : callback2()" />
</template>

<script>
import { reactive, computed } from "vue";
import Child from "./Child.vue";

export default {
  components: {
    Child,
  },
  methods: {
    callback1: () => {
      console.log("callback");
    },
    callback2: () => {
      console.log("callback2");
    },
    show: () => {
      return Math.random();
    },
  },
  setup() {
    const state = reactive({
      count: 0,
      double: computed(() => state.count * 2),
    });

    function increment() {
      if (state.count % 2) {
        state.count++;
        console.log("a :", state.count);
      } else {
        state.count++;
        console.log("az :", state.count);
      }
    }

    function show2() {
      return Math.random();
    }

    return {
      state,
      increment,
      show2,
    };
  },
};
</script>

<style scoped>
button {
  font-size: 24px;
  padding: 14px;
}
</style>
