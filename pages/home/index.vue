<template lang='pug'>
  .main
    top-bar
    .container(style="margin-top: 50px; text-align: center")
        b-button(variant="success" href="/home/application")
          i.fa.fa-edit.fa-5x
          h4(style="margin-top: 10px") Create a new Application

        b-button(style="margin-left: 150px" variant="primary" href="/home/search")
          i.fa.fa-search.fa-5x
          h4(style="margin-top: 10px") Search Your Application


</template>
<script>
    import TopBar from "../../components/TopBar"
    export default {
      components: {
        TopBar
      }
    }
</script>
<style>
</style>
