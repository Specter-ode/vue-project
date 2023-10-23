<template>
  <input class="input" :value="modelValue" @input="updateInput" />
</template>
<script>
export default {
  name: 'CustomInput',
  props: { modelValue: [String, Number] },
  methods: {
    updateInput(e) {
      this.$emit('update:modelValue', e.target.value);
    },
  },
};
</script>
<style scoped>
.input {
  width: 400px;
  border: 1px solid gray;
  padding: 12px;
  border-radius: 8px;
  font-size: 18px;
}
</style>
