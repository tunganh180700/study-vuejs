<script>
import { reactive } from 'vue'

export default {
  name: 'UIInput',

  props: {
    type: { type: String },
    placeholder: { type: String },
    name: { type: String },
    vModel: { type: String },
    heightCss: { type: String },
    borderRadiusCss: { type: String },
    borderCss: { type: String }
  },

  data() {
    return {
      styleObject: reactive({
        padding: '10px',
        height: this.heightCss,
        borderRadius: this.borderRadiusCss,
        border: this.borderCss
      })
    }
  }
}
</script>

<template>
  <div class="input">
    <input
      :value="vModel"
      @input="$emit('update:vModel', $event.target.value)"
      :type="type"
      :name="name"
      :placeholder="placeholder"
      :style="styleObject"
    />
  </div>
</template>
