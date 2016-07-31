<template lang="pug">
  canvas(height="height", width="width")
</template>

<script>
  import Chart from 'chart.js'

  export default {
    props: {
      height: String,
      width: String,
      type: {type: String, default: 'line'},
      data: Object,
      options: Object
    },
    ready() {
      setTimeout(() => {
        new Chart(this.$el, {
          type: this.type,
          data: this.data,
          options: this.options
        })
      }, 100)
    }
  }
</script>