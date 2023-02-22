<script setup>
import Article from "./Article.vue";
</script>

<template>


<h1 v-if="!articles.length">Loading...</h1>
<div v-for="(article,i) in articles" :key="i"> <Article :articleObject="article" /> </div>

</template>

<script>
export default {
    data() {
    return {
      articles:[],
      lightMode:true,
    }
  },
  methods: {
    async fetchArticles() {
      const response = await fetch("https://newsapi.org/v2/everything?q=money&apiKey=05491e75874e479d950e1d67d50b4082");
      const data = await response.json();
      this.articles = data.articles;
      console.log(this.articles);
    }
  },
  created() {
    this.fetchArticles();
  }
}
</script>

<style scoped>

</style>