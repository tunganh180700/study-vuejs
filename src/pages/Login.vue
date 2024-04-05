<script>
import UIInput from '../components/UIInput.vue'

export default {
  name: 'Login',

  components: {
    UIInput
  }
}
</script>

<template>
  <div class="login">
    <UIInput type="text" placeholder="ten dang nhap"></UIInput>
    <UIInput type="password" placeholder="mat khau"></UIInput>
  </div>
</template>

<style lang="css">
.login {
  row-gap: 10px;
}
</style>
