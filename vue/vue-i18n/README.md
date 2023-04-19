# Vue I18n

[官方文件](https://vue-i18n.intlify.dev/guide/)

## `$t` 的用法

> template 用 `$t`，script 用 `t` (自定義)。

參考：[[指南] Vue3 vue-i18n Composition API 共用方法 @地瓜大的飛翔旅程](https://smlpoints.com/guide-vue3-vue-i18n-composition-api.html)

範例程式碼：
```vue
<template>
    <span>{{ $t('nickname') }}</span>
</template>

<script setup>
import i18n from '@/js/i18n';
const { t } = i18n.global;
onMounted(() => {
    document.title = t('token manage');
});
</script>

<style lang="scss" scoped></style>
```
上列完整程式碼見 [SGO-Trainer-PHP-Temp 專案](https://github.com/Wujidadi/SGO-Trainer-PHP-Temp) 的 [`tokenPage.vue`](https://github.com/Wujidadi/SGO-Trainer-PHP-Temp/blob/main/src/resources/js/pages/tokenPage.vue)。
