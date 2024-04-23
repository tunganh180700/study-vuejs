<script>
import axios from 'axios'
import { getAllGames } from '../../config/api.js'
export default {
  name: 'GameManagement',
  data() {
    return {
      games: []
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
  <div class="container">
    <h2>Game Management</h2>
    <ul class="responsive-table">
      <li class="table-header">
        <div class="col col-1">Name</div>
        <div class="col col-2">Type</div>
        <div class="col col-3">Publisher</div>
      </li>
      <li class="table-row" v-for="game in games" :key="game.game_id">
        <div class="col col-1" data-label="Job Id">{{ game.game_name }}</div>
        <div class="col col-2" data-label="Customer Name">{{ game.game_type_id }}</div>
        <div class="col col-3" data-label="Amount">{{ game.publisher_id }}</div>
      </li>
    </ul>
  </div>
</template>
<style>
body {
  font-family: 'lato', sans-serif;
}
.container {
  width: 80%;
  margin-left: auto;
  margin-right: auto;
  padding-left: 10px;
  padding-right: 10px;
}

h2 {
  font-size: 26px;
  margin: 20px 0;
  text-align: center;
  small {
    font-size: 0.5em;
  }
}

.responsive-table {
  li {
    border-radius: 3px;
    padding: 25px 30px;
    display: flex;
    justify-content: space-between;
    margin-bottom: 25px;
  }
  .table-header {
    background-color: #95a5a6;
    font-size: 14px;
    text-transform: uppercase;
    letter-spacing: 0.03em;
  }
  .table-row {
    background-color: #ffffff;
    box-shadow: 0px 0px 9px 0px rgba(0, 0, 0, 0.1);
  }
  .col-1 {
    flex-basis: 40%;
  }
  .col-2 {
    flex-basis: 40%;
  }
  .col-3 {
    flex-basis: 25%;
  }

  @media all and (max-width: 767px) {
    .table-header {
      display: none;
    }

    li {
      display: block;
    }
    .col {
      flex-basis: 100%;
    }
    .col {
      display: flex;
      padding: 10px 0;
      &:before {
        color: #6c7a89;
        padding-right: 10px;
        content: attr(data-label);
        flex-basis: 50%;
        text-align: right;
      }
    }
  }
}
</style>
