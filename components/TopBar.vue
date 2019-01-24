<template lang="pug">
  .nav.navbar.navbar-dark.bg-dark.static-top(style="background-color:#1a6d56 !important")
    .container
      a.navbar-brand
        b-row
          b-col
            a(href="/home")
              b-img(src="/images/vm.png" rounded="circle" width="100" height="100")
          b-col.align-items-center
            h1.text-white.text-uppercase Vidya Mandir
            h4.text-white.text-uppercase Senior Secondary School
</template>

<script>
    export default {
        name: "TopBar"
    }
</script>

<style scoped>

</style>
