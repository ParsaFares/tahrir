<template>
  <div class="form float-right">
    <form action>
      <div class="col-12 col-sm-10 p-3">
        <label for="from-en" class="float-right">انگلیسی</label>
        <input
          type="text"
          id="from-en"
          name="from-en"
          placeholder="کلمه خود را جستجو کنید"
          class="w-100"
          style="height:40px"
        >
        <button class="float-left btn btn-primary mx-auto">ترجمه کن</button>
      </div>
      <div class="col-12 col-sm-10 p-3">
        <label for="from-fa" class="float-right">فارسی</label>
        <input
          type="text"
          id="from-fa"
          name="from-fa"
          placeholder="کلمه خود را جستجو کنید"
          class="w-100"
          style="height:40px"
        >
        <button class="float-left btn btn-primary mx-auto">ترجمه کن</button>
      </div>
    </form>
  </div>
</template>
<script>
export default {};
</script>
<style scoped>
.form {
  width: 50%;
  direction: rtl;
}
</style>

