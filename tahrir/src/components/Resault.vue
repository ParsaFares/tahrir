<template>
  <div class="results">
    <h1>Hey you!</h1>
    <div>
      <div class="meanings">
        <StarRating
          :star-size="28"
          :increment="0.1"
          :read-only="true"
          :rating="4.3"
          class="float-left"
        />
        <div class="mean">
          <button class="btn btn-outline-primary button">نظر بدهید</button>
          <h2>هی تو</h2>
        </div>
      </div>
      <div class="meanings">
        <StarRating
          :star-size="28"
          increment="0.1"
          read-only="true"
          rating="3.9"
          class="float-left"
        />
        <div class="mean">
          <button class="btn btn-outline-primary button">نظر بدهید</button>
          <h2>با توام</h2>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import StarRating from "vue-star-rating";

export default {
  name: "result",
  components: {
    StarRating
  }
};
</script>
<style scoped>
.button {
  margin: 0 10px;
}
.mean {
  direction: rtl;
  display: flex;
}
.meanings {
  margin: 5px;
}
StarRating {
  float: right;
}
</style>
