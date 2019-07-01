<template>
  <div id="app">
    <Header/>
    <div class="container div">
      <Search name="english"/>
      <Resault :commentIt="this.apearCommentingArea"/>
    </div>
    <CommentingArea v-if="this.show" :push="this.pushComment"/>
    <h4 class="text-center mb-4">نظرات کاربران</h4>
    <Comments :items="this.comments"/>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Search from "./components/SearchBar.vue";
import Resault from "./components/Resault.vue";
import Comments from "./components/Comments.vue";
import CommentingArea from "./components/CommentingArea.vue";

export default {
  name: "app",
  data: function() {
    return { comments: [], commentingword: "", show: false };
  },
  components: {
    Header,
    Search,
    Resault,
    Comments,
    CommentingArea
  },
  methods: {
    pushComment: function(cm) {
      //set commenting word in json
      this.comments.push(cm);
      this.show = false;
    },
    apearCommentingArea: function(word) {
      this.commentingword = word;
      this.show = true;
    }
  },
  computed: {
    //change items
    getComments: function() {
      return [];
    }
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
