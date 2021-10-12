<template>
  <validation-observer
      ref="observer"
      v-slot="{ invalid }"
  >
    <form @submit.prevent="submit">
      <vee-vuetify-input
      v-model="name"
      :label="'Name'"
      :rules="'required|alpha_spaces'"
      />

      <vee-vuetify-input
          v-model="email"
          :label="'Email'"
          :rules="'required|email'"
          :type="'email'"
      />

      <vee-vuetify-input
          v-model="password"
          :label="'Password'"
          :rules="'required|max:12|min:8'"
          :type="'password'"
      />

      <vee-vuetify-select
      v-model="select"
      :label="'Select Item'"
      :items="[
      'Item 1',
      'Item 2',
      'Item 3',
      'Item 4',
    ]"
      :rules="'required'"/>

      <vee-vuetify-checkbox
      v-model="checkbox"
      :label="'Accept Term'"
      :rules="'required'"
      />

      <v-btn
          class="mr-4"
          type="submit"
          :disabled="invalid"
      >
        submit
      </v-btn>
      <v-btn @click="clear">
        clear
      </v-btn>
    </form>
  </validation-observer>
</template>

<script>
// import {required, digits, email, max, regex} from 'vee-validate/dist/rules'
import { ValidationObserver} from 'vee-validate'
import VeeVuetifyInput from "@/vee-vuetify/vee-vuetify-input";
import VeeVuetifyCheckbox from "@/vee-vuetify/vee-vuetify-checkbox";
import VeeVuetifySelect from "@/vee-vuetify/vee-vuetify-select";

// setInteractionMode('eager')
// extend('digits', {
//   ...digits,
//   message: '{_field_} needs to be {length} digits. ({_value_})',
// })
// extend('required', {
//   ...required,
//   message: '{_field_} can not be empty',
// })
// extend('max', {
//   ...max,
//   message: '{_field_} may not be greater than {length} characters',
// })
// extend('regex', {
//   ...regex,
//   message: '{_field_} {_value_} does not match {regex}',
// })
// extend('email', {
//   ...email,
//   message: 'Email must be valid',
// })
export default {
  components: {
    VeeVuetifySelect,
    VeeVuetifyCheckbox,
    VeeVuetifyInput,
    ValidationObserver,
  },
  data: () => ({
    name: '',
    password: '',
    email: '',
    select: null,
    checkbox: null,
  }),
  methods: {
    submit() {
      this.$refs.observer.validate()
      console.log(this.$data)
    },
    clear() {
      this.name = ''
      this.password = ''
      this.email = ''
      this.select = null
      this.checkbox = null
      this.$refs.observer.reset()
    },
  },
}
</script>