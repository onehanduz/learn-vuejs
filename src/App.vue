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
    <ListCom :comments="comments" @remove="removeComment" v-if="!isLoading" />
    <div v-if="isLoading">
      <div class="d-flex justify-content-center">
        <div class="spinner-border" role="status">
          <span class="visually-hidden">Loading...</span>
        </div>
      </div>
    </div>
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
      comments: [],
      modelvisible: false,
      isLoading: false,
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
        this.isLoading = true;
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/comments?_limit=10"
        );
        this.comments = response.data;
      } catch (error) {
        console.log(error);
      } finally {
        this.isLoading = false;
      }
    },
  },
  mounted() {
    this.fetchComments();
  },
};
</script>

<style></style>
