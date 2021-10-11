<template>
  <div>
    <h1>VeeValidate Form</h1>
    <ValidationObserver v-slot="{ handleSubmit }">
      <form v-on:submit.prevent="handleSubmit(onSubmit)">

        <vee-input
          v-model="formData.name"
          v-bind:rules="'required|alpha_spaces'"
          v-bind:name="'Name'"
          v-bind:type="'name'"
        />

        <vee-input
            v-model="formData.email"
            v-bind:rules="'required|email'"
            v-bind:name="'Email'"
            v-bind:type="'email'"
        />

        <vee-input
            v-model="formData.password"
            v-bind:rules="'required|max:12|min:8'"
            v-bind:name="'Password'"
            v-bind:type="'password'"
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
import VeeSelect from "./VeeSelect.vue";
import VeeInput from "@/components/VeeInput";

export default {
  components: {
    VeeSelect,
    VeeCheckbox,
    VeeInput,
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
