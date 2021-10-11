<template>
  <ValidationProvider
      name="Name"
      v-bind:rules=rules
      v-slot="{ errors }"
  >
    <div class="form-group">
      <label>Name</label>
      <input type="text" class="form-control"
       v-model="name"
       v-on:input="$emit('input', $event.target.value)"
      />
      <span>{{ errors[0] }}</span>
    </div>
  </ValidationProvider>
</template>

<script>
export default {
  name: "VeeName",
  props: ['value', 'rules'],
  data: () => {
    return {
    name: "",
    }
  },
};
</script>
