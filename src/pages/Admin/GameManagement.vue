<script>
import axios from 'axios'
import { getAllGames, getGameById } from '../../config/api.js'
import UITable from '../../components/UITable.vue'
import IconUpdate from '../../components/icons/IconUpdate.vue'
import IconDelete from '../../components/icons/IconDelete.vue'
export default {
  name: 'GameManagement',
  components: {
    UITable,
    IconUpdate,
    IconDelete
  },
  data() {
    return {
      games: [],
      titles: ['Name', 'Type', 'Publisher', '', '']
    }
  },
  created() {
    this.getAllGames()
  },
  methods: {
    getAllGames() {
      axios
        .get(getAllGames)
        .then((response) => {
          this.games = response.data
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
  <UITable :titles="titles" :datas="games">
    <template #column0="{ data }">
      {{ data.game_name }}
    </template>
    <template #column1="{ data }">
      {{ data.game_type }}
    </template>
    <template #column2="{ data }">
      {{ data.publisher_name }}
    </template>
    <template #column3="{ data }">
      <IconUpdate width="10%" @click="this.$router.push(`edit-game/` + data.game_id)" />
    </template>
    <template #column4=""> <IconDelete width="10%" /> </template>
  </UITable>
</template>
