<template>
  <li class="post">
    <div>
      <p class="text">Title: {{ post.title }}</p>
      <p class="text">Description {{ post.description }}</p>
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
  methods: {
    handleChange() {},
  },
};
</script>

<style scoped>
.post {
  border: 2px solid goldenrod;
  padding: 10px;
  border-radius: 12px;
  width: 400px;
}
.text {
  font-size: 16px;
  font-weight: 500;
}
.btn_block {
  margin-top: 12px;
  display: flex;
  justify-content: space-around;
}
</style>
