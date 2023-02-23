<script setup>
import Article from "./Article.vue";

defineProps({
    searchValue: {
      type:String,
      required:true
    }
});

</script>

<template>
<div>
  <div v-if="!articles || !articles.length" class="flex flex-col justify-center align-center loading-wrapper">
    <h1 class="margin-bottom">Getting your News</h1>
    <img class="loading" src="../assets/images/loading-gif.gif">
  </div>

  <div v-for="(article,i) in articles" :key="i"> <div> <Article :class="{'blurred': modalStatus.active && i !== modalStatus.index}"
  @updateModalStatus="updateModalStatus"  :articleObject="article" :index="i"  /> </div> </div>
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
      this.articles = [];
      let query = this.searchValue;
      const response = await fetch(query);
      const data = await response.json();
      this.articles = data.articles;
      console.log(this.articles);
    },
    updateModalStatus(status, index) {
      this.modalStatus = {active:status, index:index};
      console.log(this.modalStatus)
    }
  },
  watch: {
    searchValue: {
      immediate: true, 
      handler (val, oldVal) {
        this.fetchArticles();
      }
    }
  },
  created() {
    this.fetchArticles();
  }
}
</script>

<style scoped>
.margin-bottom {
  margin-bottom:20px;
}
.loading-wrapper {
  height:50vh;
}
.loading {
  height:100px;
  width:100px;
}
</style>