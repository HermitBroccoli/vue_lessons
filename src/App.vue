<template>
  <div class="app">
    <h1>Страница с постами</h1>
    <div class="app_btns">
      <my-button
          @click="showDialog">Создание поста</my-button>
      <MySelect v-model="selectedSort" :options="sortOption" />
    </div>
    <my-dialog v-model:show="dialogVisible">
      <post-form @create="creatPost" />
    </my-dialog>
    <post-list :posts="posts" @remove="removePost" v-if="!isPostsLoading"/>
    <div v-else>Идёт загрузка...</div>
  </div>
</template>

<script>
import PostForm from "./components/PostForm.vue";
import PostList from "./components/PostList.vue";
import axios from "axios";

export default {
  components: {
    PostForm,
    PostList,
  },
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostsLoading: false,
      selectedSort: '',
      sortOption: [
        {value: 'title', name: 'По названию'},
        {value: 'body', name: 'По содержанию'}
      ]
    };
  },
  methods: {
    creatPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id)
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchPost() {
      try {
        this.isPostsLoading = true;
        const  response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
        this.posts = response.data;
      } catch (e) {
        alert('ошибка');
      } finally {
        this.isPostsLoading = false;
      }
    }
  },
  mounted() {
    this.fetchPost();
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}

.app_btns {
  margin: 15px 0;
  display: flex;
  justify-content: space-between;
}
</style>
