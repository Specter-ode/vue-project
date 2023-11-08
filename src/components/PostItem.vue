<template>
  <li class="post">
    <div>
      <p class="text">Title: {{ post.title }}</p>
      <p class="text">Description {{ post.body }}</p>
    </div>
    <div class="btn_block">
      <CustomButton @click="$emit('remove', post)">Delete</CustomButton>
      <CustomButton @click="handleChange">Change</CustomButton>
    </div>
  </li>
</template>
<script>
export default {
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
  emits: ['remove'],
  methods: {
    handleDelete() {},
    handleChange() {},
  },
};
</script>

<style scoped>
.post {
  border: 2px solid goldenrod;
  padding: 10px;
  border-radius: 12px;

  width: calc(100% / 4 - 9px);
  height: 180px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.text {
  font-size: 16px;
  font-weight: 500;
}
.btn_block {
  width: 100%;
  margin-top: 12px;
  display: flex;
  justify-content: space-around;
}
</style>
