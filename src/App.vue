<script setup>
import randomWords from "random-words";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
</script>

<template>
<div :class="{darkTheme:!lightTheme}">
  <Header @changeThemeStatus="changeThemeStatus" @changeSearchValue="changeSearchValue" />
  <Main :searchValue="searchValue" />
</div>



</template>

<script>
export default {
  data() {
    return {
      searchValue:"",
      lightTheme:true,
    }
  },
  methods: {
    changeThemeStatus(bool) {
      if(bool) {
        this.lightTheme = true
      }
      else {
        this.lightTheme = false;
      }
    },
    changeSearchValue(value) {
      this.searchValue = value;
    }
  },
  created() {

  }

}
</script>

<style>
.darkTheme {
  background-color:rgb(0, 0, 0);
  color:white;
}
.darkTheme .go {
  background-color: white;
  color:black;
}
.darkTheme .input-box {
  background:rgb(80, 80, 80) !important;
  color:white;
}
.darkTheme ::placeholder {
 color: white;
}
.darkTheme .container {
  color:#ECECEC;
  background-color:rgb(58, 58, 58);
}
.darkTheme .barUnderWord {
  background-color:white !important;
}
.darkTheme .used-area {
  background-color:black !important;
  color:white;
}
.darkTheme .modal .title {
  background-color:rgba(0, 0, 0, 0.8);
  color:white;
}
.darkTheme .oval-guy {
  color:white;
  background-color:rgb(81, 81, 81);
}
</style>
