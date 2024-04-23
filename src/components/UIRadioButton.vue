<script>
export default {
  name: 'UIRadioButton',
  props: {
    type: { type: String },
    id: { type: Number },
    name: { type: String },
    value: { type: Number },
    genderTitle: { type: String }
  }
}
</script>
<template>
  <input
    :type="type"
    :id="id"
    :name="name"
    :value="value"
    @change="$emit('update:value', $event.target.value)"
  />
  <label :for="id">{{ genderTitle }}</label>
</template>
