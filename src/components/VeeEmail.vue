<template>
  <ValidationProvider name="Email"
    v-bind:rules=rules
    v-slot="{ errors }"
  >
    <div class="form-group">
      <label>Email</label>
      <input type="email" class="form-control"
        v-model="email"
       v-on:input="$emit('input', $event.target.value)"
      />
      <span>{{ errors[0] }}</span>
    </div>
  </ValidationProvider>
</template>

<script>
export default {
  name: "VeeEmail",
  props: ['rules', 'value'],
  data: () => {
    return {
      email: "",
    }
  },
};
</script>
