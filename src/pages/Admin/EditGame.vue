<script>
import axios from 'axios'
import UIInput from '../../components/UIInput.vue'
import UIDropdown from '../../components/UIDropdown.vue'
import { getAllGameType, getAllPublisher, getGameById, updateGame } from '../../config/api.js'
import UIButton from '@/components/UIButton.vue'

export default {
  name: 'EditGame',
  components: {
    UIInput,
    UIDropdown,
    UIButton
  },
  data() {
    return {
      gameTypes: [],
      publishers: [],
      game_id: this.$route.params.id,
      game_name: '',
      game_type_id: 0,
      publisher_id: 0,
      isSubmitting: false
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
          this.publisher_id = response.data.data.publisher_id
          return response.data
        })
        .catch((error) => {
          console.error(error)
          return error
        })
    },
    updateInfoOfGame() {
      this.isSubmitting = true
      const payload = {
        game_name: this.game_name,
        game_type_id: this.game_type_id,
        publisher_id: this.publisher_id
      }
      axios
        .put(updateGame + this.game_id, payload)
        .then((response) => {
          return response
        })
        .catch((error) => {
          this.isSubmitting = false
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
        :choosen="game_type_id"
        @update:choosen="game_type_id = $event"
      >
        <template v-slot="{ data }">{{ data.game_type }}</template>
      </UIDropdown>
      <UIDropdown
        name="publishers"
        idDropdown="publishers"
        :list="publishers"
        valueOption="publisher_id"
        :choosen="publisher_id"
        @update:choosen="publisher_id = $event"
      >
        <template v-slot="{ data }">{{ data.publisher_name }}</template>
      </UIDropdown>
      <UIButton
        :disabled="isSubmitting"
        @click="updateInfoOfGame()"
        type="button"
        value="Update"
        paddingCss="5px"
        borderRadiusCss="20px"
        bgColor="#6fb555"
        color="white"
        widthCss="100%"
      ></UIButton>
      <div class="btn-back" @click="this.$router.push({ name: 'game-management' })">
        <p>Back</p>
      </div>
    </div>
  </div>
</template>
<style>
select {
  width: 100%;
}
</style>
