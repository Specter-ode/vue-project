<template>
  <div class="block">
    <p>Список</p>
    <ul class="list">
      <PostItem :post="post" :key="post.id" v-for="post in posts" @remove="@emit('remove', post)" />
    </ul>
  </div>
</template>
<script>
import PostItem from './PostItem.vue';
export default {
  components: { PostItem, PostItem },
  props: {
    posts: {
      type: Array,
      requared: true,
    },
  },
};
</script>

<style scoped>
.block {
  margin-top: 40px;
}
.list {
  margin-top: 10px;
  display: flex;
  flex-direction: column;
  gap: 12px;
  align-items: center;
}
</style>
