<template>
  <div id="app">
    <Header/>
    <div class="container div">
      <Search :setTranslations="setTranslations" :setLang="this.setLang"/>
      <Resault
        v-if="this.render"
        :commentIt="this.apearCommentingArea"
        :word="this.word"
        :items="this.translations"
      />
    </div>
    <CommentingArea
      v-if="this.show"
      :word="this.word"
      :translation="this.commentingword"
      :push="this.pushComment"
      :lang="this.lang"
    />
    <h4 class="text-center mb-4">نظرات کاربران</h4>
    <Comments :items="this.pureComments"/>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Search from "./components/SearchBar.vue";
import Resault from "./components/Resault.vue";
import Comments from "./components/Comments.vue";
import CommentingArea from "./components/CommentingArea.vue";
const R = require("ramda");

export default {
  name: "app",
  data: function() {
    return {
      comments: [],
      commentingword: "",
      show: false,
      word: "",
      translations: [],
      lang: "",
      pureComments: [],
      render: true
    };
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
      var i = R.map(x => x[0], this.translations).indexOf(cm.translation);
      this.translations[i][1] += cm.rating;
      this.translations[i][2] += 1;
      this.pureComments.push(cm);
      this.show = false;
    },
    apearCommentingArea: function(word) {
      this.commentingword = word;
      this.show = true;
    },
    setTranslations: function(res, word, lang) {
      this.lang = lang;
      this.comments = res.translations;
      this.word = word;
      this.translations = R.map(
        x => [
          x.translation,
          R.sum(R.map(y => y.rating, x.comments)),
          x.comments.length
        ],
        res.translations
      );
    },
    setLang: function(lang) {
      this.lang = lang;
    },
    forceRerender() {
      this.render = false;

      this.$nextTick(() => {
        this.render = true;
      });
    }
  },
  watch: {
    pureComments: function() {
      this.forceRerender();
    }
  },
  created() {
    this.pureComments = R.filter(
      x => x.translation !== undefined,
      R.map(
        x =>
          R.map(y => {
            var p = new Object();
            p.comment = y.comment;
            p.name = y.submitter_name;
            p.rating = y.rating;
            p.word = x.translation;
            return p;
          }, x.comments),
        this.comments
      )
    );
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
