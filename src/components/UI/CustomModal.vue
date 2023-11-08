<template>
  <div class="overlay" @click.stop="closeModal">
    <div class="content" @click.stop>
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CustomModal',
  props: { isModal: { type: Boolean, default: false } },
  methods: {
    closeModal() {
      this.$emit('update:isModal', false);
    },
  },
};
</script>

<style scoped>
.overlay {
  position: fixed;
  left: 0;
  top: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.4);
  display: flex;
  align-items: center;
  justify-content: center;
}
.content {
  border: 3px solid goldenrod;
  padding: 24px;
  background-color: white;
  border-radius: 12px;
  min-width: 300px;
  min-height: 100px;
}
</style>
