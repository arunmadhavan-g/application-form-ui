<template lang="pug">
    .main
      top-bar
      .container(style="margin-top: 20px; margin-bottom: 30px")
        h2(style="margin-bottom: 30px") Application Form
        b-form
          b-form-group(label="Child's Name" label-for="name")
            b-form-input(v-model="name" id="name" placeholder="Name of the Child" required)
          b-form-group(label="Date of Birth" label-for="dob")
            no-ssr
              date-picker(v-model="dob"
                          :not-before="from"
                          :not-after="to"
                          lang="en"
                          editable
                          :clearable="false"
                          date-format="DD/MM/YYYY")
          b-form-group(label="Gender" label-for="gender")
            b-form-radio-group(id="gender" v-model="gender")
              b-form-radio(value="girl") Girl
              b-form-radio(value="boy") Boy
              b-form-radio(value="neutral") Neutral
          b-form-group(label="Father's Name" label-for="fname")
            b-form-input(id="fname" placeholder="Father's Name" required v-model="father")
          b-form-group(label="Mother's Name" label-for="mname")
            b-form-input(id="mname" placeholder="Mother's Child" v-model="mother")
          b-form-group(label="Phone Number" label-for="contact")
            b-form-input(id="contact" placeholder="Phone Number" required v-model="phone")
          b-form-group(label="Email Address" label-for="email")
            b-form-input(id="email" placeholder="Email Address" required v-model="email")

          b-form-group(label="Alumni or Siblings" label-for="alumniOrSibling")
            b-form-radio-group(id="alumniOrSibling" v-model="quota" @change="setSiblingAlumni")
              b-form-radio(value="alumni") Alumni
              b-form-radio(value="sibling") Sibling
              b-form-radio(value="none") None

          b-button(variant="primary" @click="createApplication") Submit
          b-button(type="reset" style="margin-left: 20px" href="/home") Cancel



</template>

<script>
    import TopBar from "../../../components/TopBar"
    import axios from 'axios';

    export default {
      components: {
        TopBar
      },
      data(){
        return {
          from: new Date(2015, 6, 1),
          to: new Date(2016, 1, 1),
          name: null,
          father: null,
          mother: null,
          dob: new Date(2015, 6, 1),
          phone: null,
          gender: null,
          quota: "none",
          isParentAlumni: false,
          hasSiblings: false,
          email: null
        };
      },
      methods: {
        setSiblingAlumni () {
          this.isParentAlumni = this.quota === "alumni";
          this.hasSiblings = this.quota === "sibling";
        },
        async createApplication () {
          console.log("hellooooooooo");
          try {
            const data = {
              name: this.name,
              father: this.father,
              mother: this.mother,
              dob: this.dob,
              phone: this.phone,
              gender: this.gender,
              isParentAlumni: this.isParentAlumni,
              hasSiblings: this.hasSiblings,
              email: this.email
            };
            console.log("Data passed is", data);
            const result = await axios.post("http://localhost:3010/application", data, {
              headers: {'Access-Control-Allow-Origin': '*'}
            });
            console.log("saved and result", result);
          }catch (err) {
            console.log("Error while saving:", err);
          }


        }
      }
    }
</script>

<style scoped>

</style>
