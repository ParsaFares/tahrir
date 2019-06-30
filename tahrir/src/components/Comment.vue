<template>
  <div class="comment card">
    <div class="header">
      <img src="../assets/icons8-person-64.png">
      <h3>parsa</h3>
    </div>
    <div>
      <h3>The word</h3>
      <StarRating :star-size="28" :show-rating="false" :rating="4" :read-only="true"/>
      <p>
        baba in chie dige akheeeeee???baba in chie dige akheeeeee???
        baba in chie dige akheeeeee???baba in chie dige akheeeeee???
      </p>
    </div>
  </div>
</template>
<script>
import StarRating from "vue-star-rating";

export default {
  name: "comment",
  components: {
    StarRating
  }
};
</script>
<style scoped>
.header {
  background-color: bisque;
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
