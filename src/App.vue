<script setup>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
</script>

<template>
<div :class="{darkTheme:!lightTheme}">
  <Header @changeThemeStatus="changeThemeStatus" />
  <Main />
</div>



</template>

<script>
export default {
  data() {
    return {
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
  background-color:rgba(0, 0, 0, 0.75);
}
</style>
