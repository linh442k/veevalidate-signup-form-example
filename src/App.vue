<template>
  <div id="app" class="container mt-5">
    <vee-validate-form />
  </div>
</template>

<script>
import VeeValidateForm from "./components/VeeValidateForm.vue";

export default {
  name: "App",
  components: {
    VeeValidateForm,
  },
};
</script>

<style>
@import url("https://cdn.jsdelivr.net/npm/bootstrap@4.6.0/dist/css/bootstrap.min.css");

#app {
  color: #2c3e50;
}
</style>
