<script>
import UIInput from '@/components/UIInput.vue'
import axios from 'axios'

export default {
  components: {
    UIInput
  },
  data() {
    return {
      username: ''
    }
  },
  methods: {
    getUsername(){
      axios.g
    }
    signout() {
      localStorage.removeItem('token')
      localStorage.removeItem('role')
      this.$router.push('login')
    }
  }
}
</script>
<template>
  <div class="about">
    <h1>Xin chao {{ username }}</h1>
    <p @click="signout()">dang xut</p>
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
