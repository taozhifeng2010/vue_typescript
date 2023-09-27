<template>
  <div class="register">
    <div>账号注册</div>
    <input placeholder="用户名" />
    <input placeholder="密码" />
    <input placeholder="密码二次确认" />
    <button>注册</button>
    <a>已有账号？立即登录</a>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "RegisterView",
  components: {},
  // data: () => {

  // },
  methods: {},
});
</script>
<style lang="less"></style>
