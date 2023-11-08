<template>
  <div class="block" v-if="posts.length > 0">
    <p>Список</p>
    <ul class="list">
      <PostItem
        v-for="post in posts"
        :key="post.id"
        :post="post"
        @remove="$emit('remove', post)"
      />
    </ul>
  </div>
  <h2 class="no-items" v-else>NO ITEMS</h2>
</template>
<script>
import PostItem from './PostItem.vue';
export default {
  components: { PostItem },
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
  emits: ['remove'],
};
</script>

<style scoped>
.block {
  margin-top: 40px;
  padding: 0 20px;
}
.list {
  margin-top: 10px;
  display: flex;
  gap: 12px;
  align-items: center;
  flex-wrap: wrap;
}
.no-items {
  margin-top: 32px;
  color: red;
}
</style>
