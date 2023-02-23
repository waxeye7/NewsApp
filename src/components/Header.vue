<script setup>
import randomWords from "random-words";
</script>

<template>
    <div>
        <div class="flex justify-center align-center small-padding-top">
        
            <div class="search-bar relative">

                <img v-if="lightTheme" src="../assets/images/search.png">
                <img v-if="!lightTheme" src="../assets/images/search_white.png">
                
                <input v-model="searchValue" class="input-box" id="search" type="text" placeholder="Search">

                <div @click="sendSearchQuery(searchValue)" class="go absolute">Go</div>
            </div>
            <div @click="lightTheme=!lightTheme; sendThemeStatus(lightTheme);" class="theme">
                <img v-if="lightTheme" src="../assets/images/moon.png">
                <img v-if="!lightTheme" src="../assets/images/sun.png">
            </div>
        </div>


        <div class="flex align-center justify-center top-stories-and-random very-small-margin-top">
            <div v-for="(search,i) in selected_search_types" :key="i">
                <h1 @click="current_search_type_index = i; if(current_search_type_index == 0){sendSearchQuery('https://newsapi.org/v2/top-headlines?country=us&apiKey=8ff54b2755304194bea97b50b3961980')}; if(current_search_type_index == 1){searchValue=randomWords(1); sendSearchQuery(searchValue);}" :class="{selectedSearchType: current_search_type_index == i}" class="relative" >
                    {{ search }}<div :class="{shouldIDisplay: current_search_type_index == i}" class="barUnderWord"></div>
                </h1>

                
            </div>
        </div>

        <div class="flex align-center justify-center very-small-margin-top small-margin-bottom">
            <div v-for="(topic,i) in popular_topics" :key="i" >
                <div @click="current_popular_topic = i; this.searchValue=topic; sendSearchQuery('https://newsapi.org/v2/everything?q=' + topic + '&apiKey=8618ec28db794fa992149cbb4700b005');" :class="{ selectedOval: i==current_popular_topic }" class="oval-guy"> {{ topic }} </div>
            </div>
        </div>



    </div>
</template>

<script>
export default {
    data() {
        return {
            lightTheme:true,
            searchValue:"",
            current_search_type_index:0,
            selected_search_types:[
                "Top Stories",
                "Random",
            ],
            current_popular_topic:0,
            popular_topics:[
            "All",
            "Finance",
            "Sport",
            "Politics",
            ],
        }
    },
    methods:{
        sendThemeStatus(bool) {
            this.$emit('changeThemeStatus', bool)
        },
        sendSearchQuery(value) {
            this.$emit('changeSearchValue', value)
        }
    },
    created() {

        this.sendSearchQuery("https://newsapi.org/v2/top-headlines?country=us&apiKey=8ff54b2755304194bea97b50b3961980");

    }
}
</script>

<style scoped>
.small-padding-top {
    padding-top:16px;
}
.small-margin-bottom {
    margin-bottom:16px;
}
.very-small-margin-top { margin-top:10px; }
.small-margin-top { margin-top:16px; }
.search-bar {
    position:relative;
    width:70%;
}
.go {
    transform: translate(0, -50%);
    top:50%;
    right:0;
    background-color:black;
    color:white;
    border-radius:0 4px 4px 0;
    padding:9px;
    cursor: pointer;
    height:38px;
    font-size:16px;
}
.search-bar img {
    width:30px;
    height:30px;
    position:absolute;
    top:50%;
    left:2%;
    transform: translate(0, -50%);

}
.input-box {
    font-size: 20px;
    height:38px;
    border:none;
    width:100%;
    background-color:#F3F3F3;
    border-radius:6px;
    padding-left:42px;
    
}
.input-box:focus {
    outline:none;
}
.text-over-input {
    cursor:text;
    position:absolute;
    top:50%;
    left:48px;
    transform: translate(0, -46%);
    transition:0.2s ease all; 
    -moz-transition:0.2s ease all; 
    -webkit-transition:0.2s ease all;
}
.input-box:focus ~ .text-over-input {
  top:-20%;
  font-size:14px;
}
.theme {
    cursor:pointer;
    margin-left:14px;
}
.theme img {
    height:34px;
    width:34px;
}
.top-stories-and-random h1 {
    font-size:22px;
    margin-left:8px;
    margin-right:8px;
    opacity:0.5;
}
.oval-guy {
    text-align: center;
    width:74px;
    padding:8px 12px;
    margin:auto 6px;
    font-size:14px;
    background-color:#EBEBEB;
    border-radius:24px;
}
.selectedOval {
    background-color:#596FE5 !important;
    color:white !important;
}
.selectedSearchType {
    opacity:1 !important;
    z-index: 2;
}
.barUnderWord {
    position:absolute;
    display:none;
    width:44px;
    height:4px;
    background-color:#596FE5;
    bottom:0;
    left:0;
    z-index:3;
}
.shouldIDisplay {
    display:block !important;
}
</style>