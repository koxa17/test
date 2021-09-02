<template>
  <div v-if="posts.length > 0">
    <h3>Список постов!</h3>
    <post-item
      v-for="post in posts"
      :key="post.id"
      :post="post"
      @remove="$emit('remove', post)"
    ></post-item>
  </div>
  <h2 class="title__empty" v-else>Список постов пуст</h2>
  <h2 class="title__empty" >Полный</h2>
</template>

<script>
import PostItem from "./PostItem.vue";

export default {
  components: { PostItem },
  name: "PostList",
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scope>
h3 {
  text-align: center;
  margin-top: 15px;
}
.title__empty {
  text-align: center;
  color: red;
  margin-top: 15px;
}
</style>