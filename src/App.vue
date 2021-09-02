<template>
  <div class="container">
    <h1 class="main-title">Посты на Vue Js</h1>
    <div class="app__btns">
      <my-button @click="showDialog">Создать пост</my-button>
      <my-selected-list
          :options="sortOptions"
          v-model="selectedSort"
      ></my-selected-list>
    </div>
    <div class="app">
      <my-dialog v-model:show="dialogVisible">
        <post-form @create="addPost"></post-form>
      </my-dialog>
      <post-list
          v-if="isLoadingPost"
          :posts="sortedPost"
          @remove="removePost"
      ></post-list>
      <h4 v-else>Идет загрузка.....</h4>
    </div>
  </div>
</template>

<script>
import Grids from "./components/UI/Grids";
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import axios from "axios";

export default {
  name: "App",
  components: {
    Grids,
    PostForm,
    PostList,
  },

  data() {
    return {
      posts: [
        {id: '1', title: "Название поста", body: 'Описание'},
        {id: '2', title: "Название поста 2", body: 'Описание 2'},
        {id: '3', title: "Название поста 3", body: 'Описание 3'},
      ],
      dialogVisible: false,
      isLoadingPost: false,
      selectedSort: "",
      sortOptions: [
        {value: "title", name: "По Названию"},
        {value: "body", name: "По Описанию"},
        {value: "id", name: "По Id"},
      ],
    };
  },
  methods: {
    addPost: function (post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost: function (post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    showDialog: function () {
      this.dialogVisible = true;
    },
    fetchPosts: async function () {
      try {
        setTimeout(async () => {
          this.isLoadingPost = true;
          const response = await axios.get(
              "https://jsonplaceholder.typicode.com/posts?_limit=10"
          );
          this.posts = response.data;
        }, 2000);
      } catch (error) {
        alert("Ошибка!");
      } finally {
        this.isLoadingPost = false;
      }
    },
  },
  mounted: function () {
    this.fetchPosts();
  },
  computed: {
    sortedPost() {
    return [...this.posts].sort((postA, postB) => {
      return postA[this.selectedSort].localeCompare(postB[this.selectedSort]);
    });
  }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  padding: 25px;
}

.main-title {
  margin-bottom: 15px;
}

.app__btns {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

</style>