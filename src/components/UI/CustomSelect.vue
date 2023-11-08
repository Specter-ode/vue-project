<template>
  <select :value="modelValue" @change="handleChange">
    <option disabled value="">Выберите из списка</option>
    <option v-for="option in options" :key="option.value" :value="option.value">
      {{ option.name }}
    </option>
  </select>
</template>
<script>
  export default {
    name: "CustomSelect",
    props: {
      modelValue: { type: String },
      options: {
        type: Array,
        default: () => [],
      },
    },
    methods: {
      handleChange(e) {
        this.$emit("update:modelValue", e.target.value);
      },
    },
  };
</script>
<style scoped></style>
