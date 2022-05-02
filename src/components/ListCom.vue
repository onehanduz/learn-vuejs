<template>
  <div v-if="comments.length > 0">
    <commentitem
      v-for="comment in comments"
      :comment="comment"
      :key="comment.id"
      @remove="$emit('remove', comment)"
    />
  </div>
  <div v-else>no</div>
</template>

<script>
import commentitem from "@/components/Commentitems";
export default {
  components: {
    commentitem,
  },
  props: {
    comments: {
      type: Array,
      required: true,
    },
  },
};
</script>
