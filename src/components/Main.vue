<script setup>
import Article from "./Article.vue";
</script>

<template>

<div>

  <h1 v-if="!articles.length">Loading...</h1>
  <div v-for="(article,i) in articles" :key="i"> <div> <Article :class="{'blurred': modalStatus.active && i !== modalStatus.index}"
  @updateModalStatus="updateModalStatus"  :articleObject="article" :index="i"  /> </div> </div>
  {{ modalStatus }}
</div>

</template>

<script>
export default {
    data() {
      return {
        modalStatus:{active:false, index:false},
        articles:[],
        lightMode:true,
      }
  },
  computed: {

  },
  methods: {
    async fetchArticles() {
      const response = await fetch("https://newsapi.org/v2/everything?q=money&apiKey=05491e75874e479d950e1d67d50b4082");
      const data = await response.json();
      this.articles = data.articles;
      console.log(this.articles);
    },
    updateModalStatus(status, index) {
      this.modalStatus = {active:status, index:index};
      console.log(this.modalStatus)
    }
  },
  created() {
    this.fetchArticles();
  }
}
</script>

<style scoped>

</style>