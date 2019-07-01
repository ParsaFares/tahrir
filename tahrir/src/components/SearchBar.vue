<template>
  <div class="form float-right">
    <form @submit="checkForm" action="#" method="get">
      <div class="col-12 col-sm-10 p-3">
        <label for="from-en" class="float-right">انگلیسی</label>
        <input
          type="text"
          id="from-en"
          name="from-en"
          placeholder="کلمه خود را جستجو کنید"
          class="w-100"
          style="height:40px"
          v-model="wordEn"
        >
        <button type="submit" class="float-left btn btn-primary mx-auto">ترجمه کن</button>
      </div>
    </form>
    <form @submit="checkForm" action="#" method="get">
      <div class="col-12 col-sm-10 p-3">
        <label for="from-fa" class="float-right">فارسی</label>
        <input
          type="text"
          id="from-fa"
          name="from-fa"
          placeholder="کلمه خود را جستجو کنید"
          class="w-100"
          style="height:40px"
          v-model="wordFa"
        >
        <button type="submit" class="float-left btn btn-primary mx-auto">ترجمه کن</button>
      </div>
    </form>
  </div>
</template>
<script>
const axios = require("axios");

export default {
  name: "search",
  data: function() {
    return { wordEn: "", wordFa: "" };
  },
  methods: {
    checkForm: function(e) {
      e.preventDefault();
      if (this.wordEn || this.wordFa) {
        axios
          .get("http://localhost:8000/translation/get?word=s&lang=en")
          .then(res => console.log(res))
          .catch(res => console.log(res));
        return true;
      }
    }
  }
};
</script>
<style scoped>
.form {
  width: 50%;
  direction: rtl;
}
</style>

