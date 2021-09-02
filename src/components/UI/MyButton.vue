<template>
  <button class="btn" @click="createPost"><slot></slot></button>
</template>

<script>
export default {
  name: "my-button",
};
</script>

<style scope>
.btn {
  background: none;
  border: 1px solid teal;
  padding: 15px 25px;
  font-weight: bold;
}

.btn:hover {
  background: teal;
  cursor: pointer;
}
</style>