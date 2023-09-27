<template>
  <a-config-provider :getTargetContainer="getTargetContainer">
    <router-view></router-view>
  </a-config-provider>
</template>

<script>
import enUS from "ant-design-vue/es/locale/en_US";
import zhCN from "ant-design-vue/es/locale/zh_CN";
// import "moment/dist/locale/zh-cn";
import moment from "moment";
import { defineComponent, ref, watch } from "vue";
console.log(moment);

moment.locale("zh-cn");
moment.locale("en-US");

export default defineComponent({
  name: "App",
  methods: {
    getPopupContainer(el, dialogContext) {
      if (dialogContext) {
        return dialogContext.getDialogWrap();
      } else {
        return document.body;
      }
    },
  },
  setup() {
    const locale = ref(enUS.locale);
    watch(locale, (val) => {
      moment.locale(val);
    });
    return {
      enUS,
      zhCN,
      locale,
      moment,
    };
  },
});
</script>

<style lang="less">
#app {
  height: 100%;
  width: 100%;
}
</style>
