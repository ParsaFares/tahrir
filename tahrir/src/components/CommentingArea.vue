<template>
  <form @submit="checkForm" action="#" class="col-sm-5 p-3" method="post">
    <label for="from-en" class="float-right">نامی که میخواهید نمایش داده شود:</label>
    <input
      type="text"
      id="name"
      name="name"
      placeholder="نام خود را وارد کنید"
      class="w-100"
      style="height:40px"
      v-model="name"
    >
    <StarRating
      id="stars"
      :star-size="28"
      :increment="1"
      v-model="rate"
      :rating="this.rate"
      class="float-left"
    />
    <label for="ftext" class="float-right">نظرتان درباره کلمه را وارد کنید:</label>
    <textarea
      name="text"
      id="text"
      cols="30"
      rows="5"
      placeholder="نظر خود را وارد کنید"
      class="w-100"
      v-model="text"
    ></textarea>
    <button type="submit" class="btn btn-primary mx-auto">ثبت کن</button>
  </form>
</template>
<script>
import StarRating from "vue-star-rating";
const axios = require("axios");
import qs from "qs";

export default {
  name: "commentingArea",
  data: function() {
    return { name: "", text: "", rate: 5 };
  },
  props: ["push", "word", "translation", "lang"],
  components: {
    StarRating
  },
  methods: {
    checkForm: function(e) {
      e.preventDefault();
      if (this.name && this.text) {
        var params = {
          word: this.word,
          translation: this.translation,
          lang: this.lang,
          name: this.name,
          comment: this.text,
          rating: this.rate
        };
        axios
          .post("http://localhost:8000/comment/create", qs.stringify(params))
          .then(res => {
            if (res.data == "Comment successfully created") {
              this.push({
                comment: this.text,
                name: this.name,
                rating: this.rate,
                translation: this.translation
              });
            }
          });
      }
    }
  }
};
</script>
<style scoped>
* {
  direction: rtl;
  margin: 5px;
}
form {
  margin: auto;
}
#stars {
  direction: ltr;
}
</style>
