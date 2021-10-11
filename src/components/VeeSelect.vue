<template>
  <ValidationProvider
    v-bind:name=name
    v-bind:rules=rules
    v-slot="{ errors }"
  >
    <div class="form-group">
      <label>{{ name }}</label>
      <select class="form-control"
        v-model="choice"
        v-on:change="$emit('input', $event.target.value)"
      >
        <option disabled value="">Please select one</option>
        <option
          v-for="option in options"
          v-bind:value="option.value"
          v-bind:key="option.value"
        >{{option.text}}</option>

      </select>
      <span>{{ errors[0] }}</span>
    </div>
  </ValidationProvider>
</template>

<script>
export default {
  name: "VeeSelect",
  props: ["options", "name", 'rules'],
  data: () => {
    return {
      choice: "",
    }
  },
};
</script>
