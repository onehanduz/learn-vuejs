<template>
  <input :value="modelValue" @input="onInput" />
</template>

<script>
export default {
  name: "my-input",
  props: {
    modelValue: [String, Number],
  },
  methods: {
    onInput(e) {
      this.$emit("update:modelValue", e.target.value);
    },
  },
};
</script>
