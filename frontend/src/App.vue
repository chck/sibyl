<template lang="pug">
  #app.container-fluid
    .row
      .col-md-6
        h1 {{ title }}
    .row
      .col-md-12.bs-component
        .panel.panel-default
          .panel-heading {{ title }}

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
    .row
      .col-md-6
        chart(type="radar", :data="chartData", :options="chartOptions")
      .col-md-6
        chart(type="line", :data="chartData", :options="chartOptions")
    .row
      .col-md-6
        chart(type="bar", :data="chartData", :options="chartOptions")
      .col-md-6
        chart(type="polarArea", :data="chartData", :options="chartOptions")
    .row
      .col-md-6
        chart(type="pie", :data="chartData", :options="chartOptions")
      .col-md-6
        chart(type="doughnut", :data="chartData", :options="chartOptions")
</template>

<script>
  import { alert } from 'vue-strap'
  import chart from './Chart.vue'

  export default {
    components: {
      alert, chart
    },
    data() {
      return {
        title: 'Sibyl',
        showRight: false,
        showTop: false,
        user: {
          id: 'xxx',
          name: 'chck'
        },
        chartType: 'bar',
        chartData: {
          labels: ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"],
          datasets: [{
            label: '# of Votes',
            data: [12, 19, 3, 5, 2, 3],
            backgroundColor: [
              'rgba(255, 99, 132, 0.2)',
              'rgba(54, 162, 235, 0.2)',
              'rgba(255, 206, 86, 0.2)',
              'rgba(75, 192, 192, 0.2)',
              'rgba(153, 102, 255, 0.2)',
              'rgba(255, 159, 64, 0.2)'
            ],
            borderColor: [
              'rgba(255,99,132,1)',
              'rgba(54, 162, 235, 1)',
              'rgba(255, 206, 86, 1)',
              'rgba(75, 192, 192, 1)',
              'rgba(153, 102, 255, 1)',
              'rgba(255, 159, 64, 1)'
            ],
            borderWidth: 1
          }]
        },
        chartOptions: {
          scales: {
            yAxes: [{
              ticks: {
                beginAtZero:true
              }
            }]
          }
        }
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
