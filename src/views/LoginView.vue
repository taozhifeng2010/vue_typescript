<template>
  <div class="login">
    <div class="loginTitle">
      <div>
        <span class="iconfont icon-taozi"></span>
        <span>tao</span>
      </div>
      <div>
        <span>公司网址&nbsp;&nbsp;|&nbsp;&nbsp;</span>
        <span>{{ locale === "zh-cn" ? "中文" : "English" }}</span>
      </div>
    </div>
    <div class="loginFrom">
      <div class="from">
        <a-form
          :model="formState"
          name="normal_login"
          class="login-form"
          @finish="onFinish"
          @finishFailed="onFinishFailed"
        >
          <a-form-item
            label="Username"
            name="username"
            :rules="[
              { required: true, message: 'Please input your username!' },
            ]"
          >
            <a-input v-model:value="formState.username">
              <template #prefix>
                <UserOutlined class="site-form-item-icon" />
              </template>
            </a-input>
          </a-form-item>

          <a-form-item
            label="Password"
            name="password"
            :rules="[
              { required: true, message: 'Please input your password!' },
            ]"
          >
            <a-input-password v-model:value="formState.password">
              <template #prefix>
                <LockOutlined class="site-form-item-icon" />
              </template>
            </a-input-password>
          </a-form-item>

          <a-form-item>
            <a-form-item name="remember" no-style>
              <a-checkbox v-model:checked="formState.remember"
                >Remember me</a-checkbox
              >
            </a-form-item>
            <a class="login-form-forgot" href="">Forgot password</a>
          </a-form-item>

          <a-form-item>
            <a-button
              :disabled="disabled"
              type="primary"
              html-type="submit"
              class="login-form-button"
            >
              Log in
            </a-button>
            Or
            <a href="./register">register now!</a>
          </a-form-item>
        </a-form>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { reactive, computed } from "vue";
import { UserOutlined, LockOutlined } from "@ant-design/icons-vue";

interface FormState {
  username: string;
  password: string;
  remember: boolean;
}

const locale = "zh-cn";
const formState = reactive<FormState>({
  username: "",
  password: "",
  remember: true,
});
const onFinish = (values: any) => {
  console.log("Success:", values);
};

const onFinishFailed = (errorInfo: any) => {
  console.log("Failed:", errorInfo);
};
const disabled = computed(() => {
  return !(formState.username && formState.password);
});
// export default defineComponent({
//   name: "LoginView",
//   components: {},
//   // data: () => {

//   // },
//   methods: {},
// });
</script>
<style lang="less">
.login {
  width: 100%;
  height: 100%;
  padding: 10px;
  display: flex;
  flex-direction: column;
  .loginTitle {
    height: 40px;
    display: flex;
    padding: 0 40px;
    justify-content: space-between;
    .icon-taozi {
      color: pink;
    }
  }
  .loginFrom {
    flex: 1;
    padding: 0 5px;
    display: flex;
    align-items: center;
    justify-content: center;
    .from {
      border-radius: 10px;
      padding: 20px;
      box-shadow: 5px 5px 15px pink;
    }
  }
}
</style>
