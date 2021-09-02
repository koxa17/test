<template>
  <div class="post">
    <div>
      <p><strong>Название: </strong>{{ post.title }}</p>
      <p><strong>Описание: </strong>{{ post.body }}</p>
    </div>
    <my-button @click="$emit('remove', post)">Удалить</my-button>
  </div>
</template>

<script>
import MyButton from "./UI/MyButton.vue";
export default {
  components: { MyButton },
  name: "PostItem",
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scope>
.post {
  font-size: 1.2rem;
  border: 2px solid teal;
  padding: 20px 10px;
  margin-top: 15px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>