<template>
  <div>
    <nav>
      <mynavbar :open="open"></mynavbar>
      <!-- trim modifikator -->
      <router-link class="unsplash" to="/">Home</router-link> |
      <router-link class="unsplash" to="/about">About</router-link>
    </nav>
    <button @click="fetchComments">get</button>
    <mymodel v-model:show="modelvisible">
      <formcom @addComment="addComment" />
    </mymodel>
    <ListCom :comments="comments" @remove="removeComment" />
    <router-view />
  </div>
</template>

<script>
import formcom from "./components/FormCom";
import ListCom from "./components/ListCom";
import mynavbar from "@/components/navbar";
import axios from "axios";
export default {
  components: {
    formcom,
    ListCom,
    mynavbar,
  },
  data() {
    return {
      comments: [
        { id: 1, text: "hello" },
        { id: 2, text: "world" },
      ],
      modelvisible: false,
    };
  },
  methods: {
    addComment(comment) {
      this.comments.push(comment);
      this.modelvisible = false;
    },
    removeComment(comment) {
      this.comments = this.comments.filter((c) => c.id !== comment.id);
    },
    open() {
      this.modelvisible = true;
    },
    async fetchComments() {
      try {
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/comments?_limit=10"
        );
        console.log(response);
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style></style>
