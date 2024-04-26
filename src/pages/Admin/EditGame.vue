<script>
import axios from 'axios'
import UIInput from '../../components/UIInput.vue'
import { getAllGameType } from '../../config/api.js'

export default {
  name: 'EditGame',
  components: {
    UIInput
  },
  data() {
    return {
      gameTypes: []
    }
  },
  created() {
    this.getAllGameType()
  },
  methods: {
    getAllGameType() {
      axios
        .get(getAllGameType)
        .then((response) => {
          this.gameTypes = response.data
          return response
        })
        .catch((error) => {
          return error
        })
    }
  }
}
</script>
<template>
  <div class="container">
    <div class="register">
      <h1>EDIT</h1>
      <!-- <UIInput
        :vModel="password"
        @update:vModel="password = $event"
        type="password"
        placeholder="Password"
        name="password"
        heightCss="30px"
        borderRadiusCss="10px"
        borderCss="1px solid black"
      ></UIInput> -->
      <div class="input">
        <select name="cars" id="cars">
          <option v-for="i in gameTypes" :key="i.game_type_id" :value="i.game_type_id">
            {{ i.game_type }}
          </option>
        </select>
      </div>
      <div class="input">
        <select name="cars" id="cars">
          <option value="volvo">Volvo</option>
          <option value="saab">Saab</option>
          <option value="mercedes">Mercedes</option>
          <option value="audi">Audi</option>
        </select>
      </div>
    </div>
  </div>
</template>
<style>
select {
  width: 100%;
}
</style>
