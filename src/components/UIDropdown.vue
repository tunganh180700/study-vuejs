<script>
export default {
  name: 'UIDropdown',
  props: {
    name: { type: String },
    idDropdown: { type: String },
    list: { type: Array },
    valueOption: { type: String },
    choosen: { type: Number }
  },
  methods: {
    getItemValue(item) {
      return item[this.valueOption]
    },
    onChange(event) {
      const selectedValue = parseInt(event.target.value)
      console.log(typeof selectedValue)
      this.$emit('update:choosen', selectedValue)
    }
  }
}
</script>
<template>
  <div class="input">
    <select :name="name" :id="idDropdown" @change="onChange">
      <option
        v-for="(item, i) in list"
        :key="i"
        :value="getItemValue(item)"
        :selected="choosen === item[this.valueOption]"
      >
        <slot :data="item"></slot>
      </option>
    </select>
  </div>
</template>
