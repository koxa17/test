<template>
  <select v-model="modelValue" @change="changeOption" class="selected__list">
    <option value="" disabled selected>Сортировка по:</option>
    <option v-for="option in options" :key="option.value" :value="option.value">
      {{ option.name }}
    </option>
  </select>
</template>

<script>
export default {
  name: "my-selected-list",
  props: {
    modelValue: {
      type: String,
    },
    options: {
      type: Array,
      default: () => {},
    },
  },
  methods: {
    changeOption(e) {
      this.$emit("update:modelValue", e.target.value);
    },
  },
};
</script>

<style>
.selected__list {
  align-self: stretch;
}
</style>