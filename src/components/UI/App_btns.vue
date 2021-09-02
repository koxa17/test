<template>
  <div class="app__btns">
    <my-button @click="showDialog">Создать пост</my-button>
    <my-selected-list
        :options="sortOptions"
        v-model="selectedSort"
    ></my-selected-list>
  </div>
</template>

<script>
export default {
  name: "App_btns",
  data() {
    return {
      sortOptions: [
        {value: "title", name: "По Названию"},
        {value: "body", name: "По Описанию"},
        {value: "id", name: "По Id"},
      ],
      selectedSort: "",
    }
  },
  methods: {
    showDialog: function () {
      this.dialogVisible = true;
    },
  }
}
</script>

<style scoped>

</style>