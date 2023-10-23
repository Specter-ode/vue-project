<template>
  <form class="form" @submit.prevent>
    <p>Create CARD</p>
    <input class="input" type="text" placeholder="Title" v-model="post.title" name="title" />
    <CustomInput
      type="text"
      placeholder="Description"
      v-model="post.description"
      name="description"
    />
    <CustomButton @click="createPost">Создать</CustomButton>
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: '',
        body: '',
      },
    };
  },
};
</script>

<style scoped>
.form {
  margin-top: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
}
.input {
  width: 400px;
  border: 1px solid gray;
  padding: 12px;
  border-radius: 8px;
  font-size: 18px;
}
</style>
