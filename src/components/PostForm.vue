<template>
  <form @submit.prevent>
    <h2>Создание поста</h2>
    <my-input
      v-model:value="post.title"
      type="text"
      placeholder="Название"
    />
    <my-input v-model:value="post.body" type="text" placeholder="Описание" />
    <my-button
      class="btn"
      style="align-self: flex-end; margin-top: 15px"
      @click="creatPost"
      >Создать</my-button
    >
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    creatPost() {
      this.post.id = Date.now();
      this.$emit("create", this.post);
      this.post = {
        title: "",
        body: "",
      };
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
</style>
