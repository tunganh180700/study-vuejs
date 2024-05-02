<script>
import axios from 'axios'
import UIInput from '../../components/UIInput.vue'
import UIDropdown from '../../components/UIDropdown.vue'
import { getAllGameType, getAllPublisher, getGameById } from '../../config/api.js'

export default {
  name: 'EditGame',
  components: {
    UIInput,
    UIDropdown
  },
  data() {
    return {
      gameTypes: [],
      publishers: [],
      game_id: this.$route.params.id,
      game_name: '',
      game_type_id: 0
    }
  },
  created() {
    this.getAllGameType()
    this.getAllPublisher()
    this.getGameById(this.game_id)
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
    },
    getAllPublisher() {
      axios
        .get(getAllPublisher)
        .then((response) => {
          this.publishers = response.data
          return response
        })
        .catch((error) => {
          return error
        })
    },
    getGameById(game_id) {
      axios
        .get(getGameById + game_id)
        .then((response) => {
          this.game_name = response.data.data.game_name
          this.game_type_id = response.data.data.game_type_id
          console.log(response.data.data.game_type_id)
          return response.data
        })
        .catch((error) => {
          console.error(error)
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
      <UIInput
        :vModel="game_name"
        @update:vModel="game_name = $event"
        type="text"
        placeholder="Game"
        name="game_name"
        heightCss="30px"
        borderRadiusCss="10px"
        borderCss="1px solid black"
      ></UIInput>
      <UIDropdown
        name="types"
        idDropdown="types"
        :list="gameTypes"
        valueOption="game_type_id"
        v-model="this.game_type_id"
      >
        <template v-slot="{ data }">{{ data.game_type }}</template>
      </UIDropdown>
      <UIDropdown
        name="publishers"
        idDropdown="publishers"
        :list="publishers"
        valueOption="publisher_id"
      >
        <template v-slot="{ data }">{{ data.publisher_name }}</template>
      </UIDropdown>
      <button @click="this.getGameById(this.game_id)">sd</button>
    </div>
  </div>
</template>
<style>
select {
  width: 100%;
}
</style>
