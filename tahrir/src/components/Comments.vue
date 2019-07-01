<template>
  <div>
    <Comment
      v-for="item in items"
      :key="item.id"
      :name="item.name"
      :word="item.word"
      :commentBody="item.body"
      :rate="item.rating"
    />
  </div>
</template>

<script>
import Comment from "./Comment.vue";
export default {
  name: "comments",
  data: function() {
    return { items: [] };
  },
  components: { Comment },
  methods: {
    //change items
    getComments: function() {}
  }
};
</script>

<style scoped>
</style>
