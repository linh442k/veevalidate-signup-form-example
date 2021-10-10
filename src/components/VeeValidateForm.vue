<template>
  <div>
    <h1>VeeValidate Form</h1>
    <ValidationObserver v-slot="{ handleSubmit }">
      <form v-on:submit.prevent="handleSubmit(onSubmit)">
        <ValidationProvider
          name="Name"
          rules="required|alpha_spaces"
          v-slot="{ errors }"
        >
          <div class="form-group">
            <label>Name</label>
            <input type="text" class="form-control" v-model="formData.name" />
            <span>{{ errors[0] }}</span>
          </div>
        </ValidationProvider>

        <ValidationProvider
          name="Email"
          rules="required|email"
          v-slot="{ errors }"
        >
          <div class="form-group">
            <label>Email</label>
            <input type="email" class="form-control" v-model="formData.email" />
            <span>{{ errors[0] }}</span>
          </div>
        </ValidationProvider>

        <ValidationProvider
          name="Password"
          rules="required|max:12|min:8"
          v-slot="{ errors }"
        >
          <div class="form-group">
            <label>Password</label>
            <input
              type="password"
              class="form-control"
              v-model="formData.password"
            />
            <span>{{ errors[0] }}</span>
          </div>
        </ValidationProvider>

        <ValidationProvider name="Gender" rules="required" v-slot="{ errors }">
          <div class="form-group">
            <label>Gender</label>
            <select class="form-control" v-model="formData.gender">
              <option value="male">Male</option>
              <option value="female">Female</option>
              <option value="other">Other</option>
            </select>
            <span>{{ errors[0] }}</span>
          </div>
        </ValidationProvider>

        <ValidationProvider
          name="Accept Term"
          rules="required"
          v-slot="{ errors }"
        >
          <div class="form-check">
            <input
              type="checkbox"
              class="form-check-input"
              v-model="formData.acceptTerms"
            />
            <label class="form-check-label">Accept Terms</label>
          </div>
          <span>{{ errors[0] }}</span>
        </ValidationProvider>
        <br />
        <input type="submit" class="btn btn-primary" text="Submit" />
      </form>
    </ValidationObserver>
  </div>
</template>

<script>
export default {
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
