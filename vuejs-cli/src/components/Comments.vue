<template>
  <div class="container">
    <h1>Comentários</h1>
    <hr />
    <FormTodo v-on:add-todo="addComment"></FormTodo>
    <div class="list-group">
      <p v-if="comments.length <= 0">Sem comentários...</p>
      <div
        v-for="(comment, index) in allComments"
        :key="index"
        class="list-group-item"
      >
        <span class="comment__author"
          >Autor: <strong>{{ comment.author }}</strong>
        </span>
        <p>{{ comment.message }}</p>
        <div>
          <a
            v-on:click.prevent="deleteComment({ index })"
            href="#"
            title="Excluir"
            >Excluir</a
          >
        </div>
      </div>
    </div>
    <hr />
  </div>
</template>

<script>
import FormTodo from "./FormTodo.vue";

export default {
  components: {
    FormTodo,
  },
  data() {
    return {
      comments: [],
    };
  },
  methods: {
    addComment({author, message}) {
      this.comments.push({author, message});
    },
    deleteComment({ index }) {
      this.comments.splice(index, 1);
    },
  },
  computed: {
    allComments() {
      return this.comments.map((comment) => ({
        ...comment,
        author: comment.author.trim() === "" ? "Anônimo" : comment.author,
      }));
    },
  },
  watch: {
    comments(value) {
      console.log("value", value);
    },
  },
};
</script>