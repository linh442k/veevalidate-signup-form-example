<template>
  <div>
    <h1>VeeValidate Form</h1>
    <ValidationObserver v-slot="{ handleSubmit }">
      <form v-on:submit.prevent="handleSubmit(onSubmit)">

        <vee-name
          v-model="formData.name"
          v-bind:rules="'required|alpha_spaces'"
        />

        <vee-email
          v-model="formData.email"
          v-bind:rules="'required|email'"
        />

        <vee-password
          v-bind:rules="'required|max:12|min:8'"
          v-model="formData.password"
        />

        <vee-select
          v-bind:options="[
          {text: 'Male', value:'male'},
          {text: 'Female', value:'female'},
          {text: 'Other', value:'other'}]"
          v-bind:name="'Gender'"
          v-bind:rules="'required'"
          v-model="formData.gender"
        />

        <vee-checkbox
          v-bind:name="'Accept Terms'"
          v-bind:rules="'required'"
          v-model="formData.acceptTerms"
        />

        <br/>
        <input type="submit" class="btn btn-primary" text="Submit"/>
      </form>
    </ValidationObserver>
  </div>
</template>

<script>
import VeeCheckbox from "./VeeCheckbox.vue";
import VeeEmail from "./VeeEmail.vue";
import VeeName from "./VeeName.vue";
import VeePassword from "./VeePassword.vue";
import VeeSelect from "./VeeSelect.vue";

export default {
  components: {
    VeeName,
    VeeEmail,
    VeeSelect,
    VeePassword,
    VeeCheckbox,
  },

  data: () => ({
    formData: {
      name: "",
      email: "",
      password: "",
      gender: "",
      acceptTerms: null,
    },
  }),
  methods: {
    onSubmit() {
      if (this.formData.acceptTerms === false) {
        alert("You must accept the terms!!!");
        return;
      }
      console.log(this.formData);
    },
  },
};
</script>
