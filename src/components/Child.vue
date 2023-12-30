<template>
  {{ Math.random() }}
  <br />
  <button @click="$emit('someEvent')">child</button>
</template>

<script>
import { reactive, computed } from "vue";

export default {
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

    return {
      state,
      increment,
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
