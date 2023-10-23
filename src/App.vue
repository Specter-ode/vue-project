<template>
  <div>
    <PostForm @create="createPost" />
    <PostList :posts="posts" @remove="removePost" />
  </div>
</template>

<script>
import PostForm from './components/PostForm.vue';
import PostList from './components/PostList.vue';
export default {
  components: {
    PostForm,
    PostList,
  },
  data() {
    return {
      posts: [
        {
          id: 1,
          title: 'Title 11',
          body: 'description11',
        },
        {
          id: 2,
          title: 'Title 22',
          body: 'description22',
        },
        {
          id: 3,
          title: 'Title 33',
          body: 'description33',
        },
        {
          id: 4,
          title: 'Title 44',
          body: 'description44',
        },
      ],
    };
  },
  methods: {
    createPost(post) {
      if (post.title && post.description) {
        this.posts.push(post);
      }
    },
    removePost(post) {
      this.posts = this.posts.filter((el) => el.id !== post.id);
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
li {
  list-style: none;
}

/* Удалить подчеркивание и изменить цвет ссылок <a> */
a {
  text-decoration: none;
  color: #4b2c2c; /* Замените #333 на цвет, который вы хотите использовать */
}
</style>
