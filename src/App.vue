<template lang="pug">
  navbar(v-bind:avatar_url="user.avatar_url")
  #app.container-fluid
    .row
      .col-lg-2
        .row
          .col-xs-12
            img(v-bind:src="user.avatar_url")
            h1 {{user.name}}
            i.fa.fa-github.fa-lg
            i.fa.fa-facebook.fa-lg
            i.fa.fa-twitter.fa-lg
            i.fa.fa-envelope-square.fa-lg
            h6 {{user.membership}}
            h6 working for {{user.year}} years
            p
              i.fa.fa-signal.fa-fw
              span
                b Rank:
              span.detail-value {{user.scores.total_rank}}
          .col-xs-12
            .panel.panel-default
              .panel-heading
                b Score
                span.detail-value {{totalScore}}
                  i.fa.fa-star.fa-fw
              .list-group
                .list-group-item
                  a(href="#") Github
                    span.detail-value {{user.scores.github}}
                      i.fa.fa-star.fa-fw
                .list-group-item
                  a(href="#") Qiita
                    span.detail-value {{user.scores.qiita}}
                      i.fa.fa-star.fa-fw
                .list-group-item
                  a(href="#") SlideShare
                    span.detail-value {{user.scores.slide_share}}
                      i.fa.fa-star.fa-fw
                .list-group-item
                  a(href="#") Stack Overflow
                    span.detail-value {{user.scores.stack_overflow}}
                      i.fa.fa-star.fa-fw
      .col-lg-10
        .row
          .col-xs-10
            .panel.panel-default
              .panel-heading
                b Commits
              chart(height="100", type="line", :data="chartData", :options="chartOptions")
          .col-xs-5
            .panel.panel-default
              .panel-heading
                b Languages
              chart(type="doughnut", :data="chartData", :options="chartOptions")
          .col-xs-5
            .panel.panel-default
              .panel-heading
                b Skills
              chart(type="radar", :data="chartData", :options="chartOptions")
</template>

<script>
  import {alert} from 'vue-strap'
  import chart from './Chart.vue'
  import navbar from './NavBar.vue'

  export default {
    components: {
      alert, chart, navbar
    },
    data() {
      return {
        title: 'Sibyl',
        showRight: false,
        showTop: false,
        user: {
          id: 'xxx',
          name: 'chck',
          membership: 'membership',
          avatar_url: 'https://avatars.githubusercontent.com/u/7288735?v=3',
          year: 10,
          scores: {
            total_rank: "1020/1020",
            github: 99,
            qiita: 32,
            slide_share: 45,
            stack_overflow: 102
          }
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
                beginAtZero: true
              }
            }]
          }
        }
      }
    },
    computed: {
      totalScore() {
        const scores = this.user.scores;
        return scores.github + scores.qiita + scores.stack_overflow + scores.slide_share;
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

  .detail-value
    float: right
</style>
