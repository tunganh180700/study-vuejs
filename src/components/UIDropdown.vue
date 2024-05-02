<script>
export default {
  name: 'UIDropdown',
  props: {
    name: { type: String },
    idDropdown: { type: String },
    list: { type: Array },
    valueOption: { type: String }
  },
  methods: {
    getItemValue(item) {
      return item[this.valueOption]
    }
  }
}
</script>
<template>
  <div class="input">
    <select :name="name" :id="idDropdown">
      <option v-for="(item, i) in list" :key="i" :value="getItemValue(item)">
        <slot :data="item"></slot>
      </option>
    </select>
  </div>
</template>
