<script>
import UIInput from '@/components/UIInput.vue'
import axios from 'axios'
import { getUserAPI } from '../config/api.js'

export default {
  components: {
    UIInput
  },
  data() {
    return {
      user: {}
    }
  },
  created() {
    this.getUser()
  },
  methods: {
    getUser() {
      axios
        .get(getUserAPI, { headers: { Authorization: 'Bearer ' + localStorage.getItem('token') } })
        .then((r) => {
          this.user = r.data.data
          return r
        })
        .catch((e) => {
          return e
        })
    },
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
    <h1>Xin chao {{ user?.first_name }} {{ user?.last_name }}</h1>
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
