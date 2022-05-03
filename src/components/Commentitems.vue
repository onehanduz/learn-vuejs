<template>
  <div>
    <b>msg : {{ comment.body }}</b> <br />
    <b>name : {{ comment.name }}</b> <br />
    <b>email : {{ comment.email }}</b> <br />
    <button class="btn btn-outline-danger" @click="$emit('remove', comment)">
      Delete
    </button>
  </div>
</template>

<script>
export default {
  props: {
    comment: {
      type: Object,
      required: true,
    },
  },
};
</script>
