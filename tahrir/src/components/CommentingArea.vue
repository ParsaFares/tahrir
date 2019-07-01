<template>
  <form action class="col-sm-5 p-3">
    <label for="from-en" class="float-right">نامی که میخواهید نمایش داده شود:</label>
    <input
      type="text"
      id="name"
      name="name"
      placeholder="نام خود را وارد کنید"
      class="w-100"
      style="height:40px"
    >
    <StarRating id="stars" :star-size="28" :increment="1" :rating="5" class="float-left"/>
    <label for="ftext" class="float-right">نظرتان درباره کلمه را وارد کنید:</label>
    <textarea
      name="text"
      id="text"
      cols="30"
      rows="5"
      placeholder="نظر خود را وارد کنید"
      class="w-100"
    ></textarea>
    <button class="btn btn-primary mx-auto">ثبت کن</button>
  </form>
</template>
<script>
import StarRating from "vue-star-rating";

export default {
  name: "commentingArea",
  props: ["push"],
  components: {
    StarRating
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
