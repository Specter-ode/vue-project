<template lang="">
  <button class="btn" type="button"><slot></slot></button>
</template>
<script>
export default { name: 'CustomButton' };
</script>
<style scoped>
.btn {
  padding: 10px 15px;
  border: 2px solid goldenrod;
  border-radius: 12px;
  background-color: blanchedalmond;
  font-size: 18px;
  font-weight: 600;
}
</style>
