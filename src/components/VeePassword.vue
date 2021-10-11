<template>
  <ValidationProvider
      name="Password"
      v-bind:rules=rules
      v-slot="{ errors }"
  >
    <div class="form-group">
      <label>Password</label>
      <input type="password" class="form-control"
       v-model="password"
       v-on:input="$emit('input', $event.target.value)"
      />
      <span>{{ errors[0] }}</span>
    </div>
  </ValidationProvider>
</template>

<script>
export default {
  name: "VeePassword",
  props: ['rules', 'value'],
  data: () => {
    return {
      password: "",
    }
  },
};
</script>
