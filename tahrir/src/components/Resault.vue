<template>
  <div class="results">
    <h1>{{word}}</h1>
    <div>
      <div class="meanings" v-for="item of items" :key="item.id">
        <StarRating
          :star-size="28"
          :increment="0.1"
          :read-only="true"
          :rating="item.rate"
          class="float-left"
        />
        <div class="mean">
          <button class="btn btn-outline-primary button" @click="commentIt(word)">نظر بدهید</button>
          <h2>{{item.mean}}</h2>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import StarRating from "vue-star-rating";

export default {
  name: "result",
  props: ["commentIt"],
  data: function() {
    return { word: "", items: [] };
  },
  components: {
    StarRating
  },
  methods: {
    getWord: function() {}
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
