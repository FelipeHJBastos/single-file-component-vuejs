<template>
  <div class="form-todo form-group">
    <p>
      <input
        v-model="author"
        placeholder="Autor"
        type="text"
        name="author"
        class="form-control"
      />
    </p>
    <p>
      <textarea
        v-model="message"
        placeholder="Comentário"
        class="form-control"
        name="message"
      ></textarea>
    </p>
    <button
      v-on:click.prevent="addComment"
      type="submit"
      class="btn btn-primary"
    >
      Comentar
    </button>
  </div>
</template>

<script>
export default {
  data(){
    return {
      name: '',
      message: '',
    }
  },
  methods: {
    addComment() {
      if (this.message.trim() !== "") {
        this.$emit('add-todo', {
          author: this.author,
          message: this.message,
        })
      }

      this.author = "";
      this.message = "";
    },
  }
};
</script>