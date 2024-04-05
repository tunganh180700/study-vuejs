<script>
import UIInput from '@/components/UIInput.vue'

export default {
  components: {
    UIInput
  }
}
</script>
<template>
  <div class="about">
    <h1>This is an about page</h1>
    <UIInput type="text" placeholder="ten dang nhap"></UIInput>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
