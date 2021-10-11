<template>
  <ValidationProvider
      v-bind:name=name
      v-bind:rules=rules
      v-slot="{ errors }"
  >
    <div class="form-group">
      <label>{{name}}</label>
      <input v-bind:type="type" class="form-control"
             v-model="text"
             v-on:input="$emit('input', $event.target.value)"
      />
      <span>{{ errors[0] }}</span>
    </div>
  </ValidationProvider>
</template>

<script>
export default {
  name: "VeeInput",
  props: ['rules', 'value', 'name', 'type'],
  data: () => {
    return {
      text: "",
    }
  },
}
</script>

<style scoped>

</style>