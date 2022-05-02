<template>
  <div>
    <form>
      <my-input
        v-model="comment.email"
        type="text"
        placeholder="email"
        name="email"
      />
      <my-input
        v-model="comment.text"
        type="text"
        placeholder="msg"
        name="text"
      />
      <my-button @click="create">yuborish</my-button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      comment: {
        text: "",
        email: "",
      },
    };
  },
  methods: {
    create(e) {
      e.preventDefault();
      e.stopPropagation();
      this.$emit("addComment", this.comment);
      this.comment = {
        text: "",
        email: "",
      };
    },
  },
};
</script>
