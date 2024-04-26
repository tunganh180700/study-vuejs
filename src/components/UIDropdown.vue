<script>
export default {
  name: 'UIDropdown',
  props: {
    name: { type: String },
    idDropdown: { type: String },
    list: { type: Array }
  }
}
</script>
<template>
  <div class="input">
    <select :name="name" :id="idDropdown">
      <option v-for="item in list" :key="i.game_type_id" :value="i.game_type_id">
        {{ i.game_type }}
      </option>
    </select>
  </div>
  s
</template>
