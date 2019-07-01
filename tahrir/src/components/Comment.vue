<template>
  <div class="comment card">
    <div class="header">
      <img src="../assets/icons8-person-96.png">
      <h3>{{name}}</h3>
    </div>
    <div>
      <h3>{{"\"" + word + "\""}}</h3>
      <StarRating :star-size="28" :show-rating="false" :rating="rate" :read-only="true"/>
      <p class="float-right" style="margin:5px">{{commentBody}}</p>
    </div>
  </div>
</template>
<script>
import StarRating from "vue-star-rating";

export default {
  name: "comment",
  props: ["name", "word", "rate", "commentBody"],
  components: {
    StarRating
  }
};
</script>
<style scoped>
.header {
  float: right;
  direction: rtl;
}
h3 {
  display: block;
  float: right;
}
img {
  height: 50px;
  display: block;
}
.comment {
  width: 45%;
  margin: 10px;
  display: inline-block;
  padding: 20px 10px;
}
</style>
