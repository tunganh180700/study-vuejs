<script>
import { reactive } from 'vue'

export default {
  name: 'UIInput',

  props: {
    type: { type: String },
    placeholder: { type: String }
  },

  data() {
    return {
      styleObject: reactive({
        height: '30px',
        borderRadius: '5px',
        border: '1px solid black'
      })
    }
  }
}
</script>

<template>
  <div class="input">
    <input :type="type" :placeholder="placeholder" :style="styleObject" />
  </div>
</template>
