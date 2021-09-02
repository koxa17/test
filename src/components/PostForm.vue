<template>
  <form @submit.prevent>
    <h2>Создайте новый пост!</h2>
    <my-input type="text" placeholder="Название" v-model="post.title" />
    <my-input type="text" placeholder="Описание" v-model="post.body" />
    <my-button @click="createPost" :style="btnForm">Создать</my-button>
  </form>
</template>

<script>
import MyButton from "./UI/MyButton.vue";
export default {
  components: { MyButton },
  name: "PostForm",
  data: () => {
    return {
      post: {
        title: "",
        body: "",
      },
      btnForm: {
        "margin-top": "15px",
        "align-self": "flex-end",
      },
    };
  },
  methods: {
    createPost: function () {
      if (this.post.title && this.post.body) {
        this.post.id = Date.now();
        this.$emit("create", this.post);
        this.post = {
          title: "",
          body: "",
        };
      } else {
        alert("Заполните поля");
      }
    },
  },
};
</script>

<style>
form {
  display: flex;
  flex-direction: column;
  padding-bottom: 15px;
}
.input {
  border: 1px solid teal;
  padding: 10px;
  font-size: 18px;
  width: 100%;
  margin-top: 10px;
}
</style>