<template>
  <main class="main">
    <h1 class="title">Posts page</h1>
    <div class="btn-box">
      <CustomButton @click="showModal">Create post</CustomButton>
      <CustomSelect v-model="selectedSort" :options="sortOptions" />
    </div>

    <CustomModal v-if="isModal" v-model:isModal="isModal">
      <PostForm @create="createPost" />
    </CustomModal>
    <PostList :posts="posts" @remove="removePost" v-if="!isPostLoading" />
    <h2 class="loading" v-if="isPostLoading">Is loading...</h2>
  </main>
</template>

<script>
  import axios from "axios";
  import PostForm from "./components/PostForm.vue";
  import PostList from "./components/PostList.vue";
  import CustomButton from "./components/UI/CustomButton.vue";
  import CustomModal from "./components/UI/CustomModal.vue";
  import CustomSelect from "./components/UI/CustomSelect.vue";

  export default {
    components: {
      PostForm,
      PostList,
      CustomModal,
      CustomButton,
      CustomSelect,
    },
    data() {
      return {
        posts: [],
        isModal: false,
        isPostLoading: false,
        selectedSort: "",
        sortOptions: [
          { value: "title", name: "По названия" },
          { value: "body", name: "По описанию" },
        ],
      };
    },
    methods: {
      createPost(post) {
        this.posts.push(post);
        this.isModal = false;
      },
      removePost(post) {
        console.log("removePost post: ", post);
        this.posts = this.posts.filter((el) => el.id !== post.id);
      },
      showModal() {
        this.isModal = true;
      },

      async getPosts() {
        try {
          this.isPostLoading = true;
          const response = await axios.get(
            "https://jsonplaceholder.typicode.com/posts?_limit=12",
          );
          console.log("response: ", response);
          this.posts = response.data;
        } catch (error) {
          console.log("error: ", error);
        } finally {
          this.isPostLoading = false;
        }
      },
    },
    mounted() {
      this.getPosts();
    },
    watch: {
      selectedSort(newValue) {
        [...this.posts].sort((a, b) => a[newValue]?.localeCompare(b[newValue]));
      },
    },
    //     computed: {
    // handleSort(newValue) {
    //   [...this.posts].sort((a, b) => a[newValue]?.localeCompare(b[newValue]));
    // },
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

  a {
    text-decoration: none;
    color: #4b2c2c;
  }

  .main {
    height: 100vh;
  }
  .title {
    margin-top: 12px;
    margin-bottom: 24px;
  }
  .loading {
    font-size: 40px;
    margin: 40px 0;
    text-align: center;
  }
  .btn-box {
    display: flex;
    justify-content: space-around;
  }
</style>
