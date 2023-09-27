<template>
  <div class="home">
    <div>{{ value }}</div>
    <a-button @click="addFn">+1</a-button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { Button } from "ant-design-vue";

export default defineComponent({
  name: "HomeView",
  components: {
    AButton: Button,
  },
  data: () => {
    return {
      value: 0,
    };
  },
  methods: {
    addFn() {
      this.value++;
    },
  },
});
</script>
<style lang="less">
.home {
  width: 100%;
  height: 100%;
}
</style>
