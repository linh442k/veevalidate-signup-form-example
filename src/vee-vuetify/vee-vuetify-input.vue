<template>
  <validation-provider
      v-slot="{ errors }"
      :name=label
      :rules=rules
  >
    <v-text-field
        :value="value"
        @input="$emit('input', text)"
        v-model="text"
        :error-messages="errors"
        :type="type"
        :label="label"
    ></v-text-field>
  </validation-provider>
</template>

<script>
export default {
  props: {
    value:{

    },
    label:{
      type: String
    },
    rules:{
      type: [String, Object]
    },
    type:{
      type: String,
      default: "text"
    }
  },
  data: () => {
    return {
      text: "",
    }
  }
}
</script>