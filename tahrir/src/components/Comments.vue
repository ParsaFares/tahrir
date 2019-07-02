<template>
  <div>
    <Comment
      v-for="item of this.items"
      :key="item.id"
      :name="item.name"
      :word="item.translation"
      :commentBody="item.comment"
      :rate="item.rating"
    />
  </div>
</template>

<script>
import Comment from "./Comment.vue";

export default {
  name: "comments",
  props: ["items"],
  components: { Comment }
};
</script>

<style scoped>
</style>
