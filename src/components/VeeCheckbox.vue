<template>
  <ValidationProvider
    v-bind:name=name
    v-bind:rules=rules
    v-slot="{ errors }"
  >
    <div class="form-check">
      <input
        type="checkbox"
        class="form-check-input"
        v-model="accept"
        v-on:change="$emit('input', $event.target.checked)"
      />
      <label class="form-check-label">{{ name }}</label>
    </div>
    <span>{{ errors[0] }}</span>
  </ValidationProvider>
</template>

<script>
export default {
  name: "VeeCheckbox",
  props: ["checked", "rules", "name"],
  data: () => {
    return {
      accept: "",
    }
  },
};
</script>
