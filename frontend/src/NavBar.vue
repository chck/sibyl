<template lang="pug">
  nav.navbar.navbar-default
    .container-fluid
      .navbar-header
        button(type="button").navbar-toggle.collapsed(data-toggle="collapse", data-target="#bs-example-navbar-collapse-1", aria-expanded="false")
          span.sr-only Toggle navi
          span.icon-bar
          span.icon-bar
          span.icon-bar
        a.navbar-brand(href="#")
          i.fa.fa-eye Sibyl
      .collapse.navbar-collapse#bs-example-navbar-collapse-1
        form.navbar-form.navbar-left
          .form-group
            input(type="text", placeholder="Search").form-control
          button(type="submit").btn.btn-default Submit
        ul.nav.navbar-nav.navbar-left
          li
            a(href="#")
              b Users
        ul.nav.navbar-nav.navbar-right
          li.dropdown
            a.dropdown-toggle(href="#", data-toggle="dropdown", role="button", aria-haspopup="true", aria-expanded="false")
              img(v-bind:src="avatar_url").dropdown-avatar
              span.caret
            ul.dropdown-menu
              li
                a(href="#") Action
              li
                a(href="#") Action
              li
                a(href="#") Action
              li(role="separator").divider
              li
                a(href="#") Separated
</template>

<script>
  export default {
    props: {
      avatar_url: String
    }
  }

</script>

<style lang="stylus">
  .dropdown-toggle
    height: 50px
  .dropdown-avatar
    height: 30px
</style>