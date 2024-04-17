<script>
export default {
  name: 'UIRadioButton',
  props: {
    type: { type: String },
    id: { type: String },
    name: { type: String },
    value: { type: String },
    genderTitle: { type: String }
  }
}
</script>
<template>
  <div>
    <input :type="type" :id="id" :name="name" :value="value" />&nbsp
    <label :for="id">{{ genderTitle }}</label>
  </div>
</template>
