<template lang="pug">
  .main
    top-bar
    .container(style="margin-top: 20px; margin-bottom: 30px")
      h2(style="margin-bottom: 30px") Application Details
      h3 {{ this.data }}




</template>

<script>
  import TopBar from "../../../../components/TopBar"
  import axios from 'axios';

  export default {
    components: {
      TopBar
    },
    async mounted() {
      this.data = (await axios.get(`http://localhost:3010/application/${this.id}`)).data;
      console.log("data received:", this.data)
    },
    asyncData (context) {
      return { id: context.params.id,
                data: null}
    },
    methods: {
    }
  }
</script>

<style scoped>

</style>
