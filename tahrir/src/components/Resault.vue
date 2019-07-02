<template>
  <div class="results">
    <h1>{{this.word}}</h1>
    <div>
      <div class="meanings" v-for="item of items" :key="item.id">
        <StarRating
          :star-size="28"
          :increment="0.1"
          :read-only="true"
          :rating="item[1]/(item[2]!=0?item[2]:1)"
          class="float-left"
        />
        <div class="mean">
          <button class="btn btn-outline-primary button" @click="commentIt(item[0])">نظر بدهید</button>
          <h2>{{item[0]}}</h2>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import StarRating from "vue-star-rating";

export default {
  name: "result",
  props: ["commentIt", "word", "items"],
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
