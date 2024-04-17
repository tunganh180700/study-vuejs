<script>
import { reactive } from 'vue'
export default {
  name: 'UIButton',
  props: {
    type: { type: String },
    value: { type: String },
    paddingCss: { type: String },
    borderRadiusCss: { type: String },
    bgColor: { type: String },
    color: { type: String },
    widthCss: { type: String }
  },
  data() {
    return {
      styleObject: reactive({
        padding: this.paddingCss,
        borderRadius: this.borderRadiusCss,
        backgroundColor: this.bgColor,
        color: this.color,
        width: this.widthCss
      })
    }
  }
}
</script>
<template>
  <input :type="type" :value="value" :style="styleObject" />
</template>
