<script>
import axios from 'axios'
import UIInput from '../components/UIInput.vue'
import UIButton from '../components/UIButton.vue'
import UIRadioButton from '../components/UIRadioButton.vue'
import { registerAPI } from '../config/api.js'
export default {
  name: 'Register',
  components: { UIInput, UIButton, UIRadioButton },
  data() {
    return {
      options: [
        { text: 'Male', value: 1 },
        { text: 'Female', value: 2 }
      ],
      firstname: '',
      lastname: '',
      username: '',
      password: '',
      gender: 1,
      isSubmitting: false
    }
  },
  methods: {
    register() {
      this.isSubmitting = true
      const payload = {
        first_name: this.firstname,
        last_name: this.lastname,
        username: this.username,
        password: this.password,
        gender: this.gender
      }
      axios
        .post(registerAPI, payload)
        .then((response) => {
          this.$router.push('login')
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
    <div class="register">
      <h1>REGISTER</h1>
      <UIInput
        :vModel="firstname"
        @update:vModel="firstname = $event"
        type="text"
        placeholder="First-name"
        name="firstname"
        heightCss="30px"
        borderRadiusCss="10px"
        borderCss="1px solid black"
      ></UIInput>
      <UIInput
        :vModel="lastname"
        @update:vModel="lastname = $event"
        type="text"
        placeholder="Last-name"
        name="lastname"
        heightCss="30px"
        borderRadiusCss="10px"
        borderCss="1px solid black"
      ></UIInput>
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
      <div class="radio-group">
        <UIRadioButton
          v-for="option in options"
          type="radio"
          :id="option.value"
          name="gender"
          :value="option.value"
          :genderTitle="option.text"
          @update:value="gender = $event"
        ></UIRadioButton
        ><br />
      </div>
      <UIButton
        :disabled="isSubmitting"
        @click="register()"
        type="button"
        value="Register"
        paddingCss="5px"
        borderRadiusCss="20px"
        bgColor="#6fb555"
        color="white"
        widthCss="100%"
      ></UIButton>
      <p>Selected: {{ gender }}</p>

      <div class="btn-back" @click="this.$router.push('login')">
        <p>Back</p>
      </div>
    </div>
  </div>
</template>
<style lang="css">
.register {
  justify-content: center;
  align-items: center;
  padding: 10px;
  border: 1px solid black;
  display: flex;
  flex-direction: column;
  row-gap: 10px;
}
.radio-group {
  display: flex;
  column-gap: 10px;
}
</style>
