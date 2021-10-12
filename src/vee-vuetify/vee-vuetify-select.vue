<template>
  <validation-provider
      v-slot="{ errors }"
      name="select"
      :rules="rules"
  >
    <v-select
        :value="value"
        @change="$emit('input', choice)"
        v-model="choice"
        :items="items"
        :error-messages="errors"
        :label="label"
        data-vv-name="select"
    ></v-select>
  </validation-provider>
</template>

<script>
export default {
  // props: ["items", "value", "label", 'rules'],
  props: {
    items: {
      type: [Array, String, Object]
    },
    value: {

    },
    label: {
      type: String,
    },
    rules: {
      type: [String, Object]
    },
  },
  data: () => {
    return {
      choice: "",
    }
  },
};
</script>