<template lang="pug">
  #app
    h1 {{ msg }}

    button.btn.btn-success.btn-lg(@click="showRight = !showRight") Click to toggle alert on right
    button.btn.btn-danger.btn-lg(@click="showTop = !showTop") Click to toggle alert on top

    alert(type="success", width="400px", placement="top-right", dismissable, :show.sync="showRight", :duration="3000")
      span.glyphicon.glyphicon-ok-sign.alert-icon-float-left
      strong Well Done!
      p You successfully read this important alert message.

    alert(type="danger", width="400px", placement="top", dismissable, :show.sync="showTop", :duration="3000")
      span.glyphicon.glyphicon-info-sign.alert-icon-float-left
      strong Heads up!
      p This alert needs your attention.
</template>

<script>
  import { alert } from 'vue-strap'

  export default {
    components: {
      alert
    },
    data () {
      return {
        msg: 'Hello Vue!',
        showRight: false,
        showTop: false
      }
    }
  }
</script>

<style lang="stylus">
  body
    font-family: Helvetica, sans-serif

  .alert-icon-float-left
    font-size: 32px
    float: left
    margin-right: 5px
</style>
