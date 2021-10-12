<template>
  <validation-provider
      v-slot="{ errors }"
      :rules=rules
      name="checkbox"
  >
    <v-checkbox
        :value="value"
        @change="$emit('input', checkbox)"
        v-model="checkbox"
        :error-messages="errors"
        :label="label"
        type="checkbox"
    ></v-checkbox>
  </validation-provider>
</template>
<script>
export default {
  // props: ["value", "label", "rules"],
  props: {
    value: {

    },
    label: {
      type: String,
    },
    rules: {
      type: [String, Object]
    }
  },
  data: () => {
    return {
      checkbox: "",
    }
  }
}
</script>