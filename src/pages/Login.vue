<script>
import axios from 'axios'
import UIInput from '../components/UIInput.vue'
import UIButton from '../components/UIButton.vue'
import { loginAPI } from '../config/api.js'

export default {
  name: 'Login',

  components: {
    UIInput,
    UIButton
  },
  data() {
    return {
      username: '',
      password: '',
      isSubmitting: false
    }
  },
  methods: {
    login() {
      this.isSubmitting = true
      const payload = {
        username: this.username,
        password: this.password
      }
      axios
        .post(loginAPI, payload)
        .then((response) => {
          localStorage.setItem('token', response.data.token)
          localStorage.setItem('role', response.data.role)
          this.$router.push('about')

          return response
        })
        .catch((error) => {
          this.isSubmitting = false
          return error
        })
    }
  }
}
</script>

<template>
  <div class="container">
    <div class="login">
      <h1>LOGIN</h1>
      <UIInput
        :vModel="username"
        @update:vModel="username = $event"
        type="text"
        placeholder="Username"
        name="username"
        heightCss="30px"
        borderRadiusCss="10px"
        borderCss="1px solid black"
      ></UIInput>
      <UIInput
        :vModel="password"
        @update:vModel="password = $event"
        type="password"
        placeholder="Password"
        name="password"
        heightCss="30px"
        borderRadiusCss="10px"
        borderCss="1px solid black"
      ></UIInput>
      <UIButton
        :disabled="isSubmitting"
        @click="login()"
        type="button"
        value="Login"
        paddingCss="5px"
        borderRadiusCss="20px"
        bgColor="#6fb555"
        color="white"
        widthCss="100%"
      ></UIButton>
      <div class="btn-register" @click="this.$router.push('register')">
        <p>Register</p>
      </div>
    </div>
  </div>
</template>

<style lang="css">
.login {
  padding: 10px;
  border: 1px solid black;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  row-gap: 10px;
}
.btn-register {
  cursor: pointer;
}

.btn-register:hover {
  color: red;
}
</style>
