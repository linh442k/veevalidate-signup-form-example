<template>
  <v-app>
    <v-main>
      <v-container>
<!--        <vee-validate-form/>-->
        <misc-vee-validate/>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
// import VeeValidateForm from "./components/VeeValidateForm.vue";
import MiscVeeValidate from "@/vee-vuetify/misc-vee-validate";

export default {
  name: "App",
  components: {
    MiscVeeValidate,
    // VeeValidateForm,
  },
};
</script>

