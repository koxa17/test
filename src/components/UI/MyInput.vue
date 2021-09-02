<template>
  <input type="text" class="input" :value="modelValue" @input="updateInput" />
</template>

<script>
export default {
  name: "my-input",
  props: {
    modelValue: [String, Number],
  },
  methods: {
    updateInput: function (event) {
      this.$emit("update:modelValue", event.target.value);
    },
  },
};
</script>

<style>
</style>