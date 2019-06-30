<template>
  <div id="app">
    <Header/>
    <div class="container div">
      <Search name="english"/>
      <Resault/>
    </div>
    <h4 class="text-center mb-4">نظرات کاربران</h4>
    <Comments/>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Search from "./components/SearchBar.vue";
import Resault from "./components/Resault.vue";
import Comments from "./components/Comments.vue";

export default {
  name: "app",
  components: {
    Header,
    Search,
    Resault,
    Comments
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}
.div {
  display: inline-block;
  margin: 20px;
}
Comment {
  width: 100%;
}
</style>
