<script setup>

</script>

<template>
    <div>
        <div class="flex justify-center align-center small-margin-top">
        
            <div class="search-bar">
                <img src="../assets/search.svg">
                
                <input class="input-box" id="search" type="text" placeholder="Search">
            </div>
            <div class="theme">
                <img src="../assets/moon.png">
            </div>
        </div>


        <div class="flex align-center justify-center top-stories-and-random very-small-margin-top">
            <div v-for="(search,i) in selected_search_types" :key="i">

                <h1 @click="current_search_type = i" :class="{selectedSearchType: current_search_type == i}" class="relative" >
                    {{ search }}<div :class="{shouldIDisplay: current_search_type == i}" class="barUnderWord"></div>
                </h1>

                
            </div>
        </div>

        <div class="flex align-center justify-center very-small-margin-top small-margin-bottom">
            <div v-for="(topic,i) in popular_topics" :key="i" >
                <div @click="oval => oval.target.classList.toggle('selectedOval')" :class="{ selectedOval: i==0 }" class="oval-guy"> {{ topic }} </div>
            </div>
        </div>



    </div>
</template>

<script>
export default {
    data() {
        return {
            current_search_type:0,
            selected_search_types:[
                "Top Stories",
                "Recent",
                "Random",
            ],

            popular_topics:[
            "All",
            "Finance",
            "Sport",
            "Politics",
            ],
        }
    },
    methods:{
        makeAllOpacityLow() {

        }
    }
}
</script>

<style scoped>
.small-margin-bottom {
    margin-bottom:16px;
}
.very-small-margin-top { margin-top:10px; }
.small-margin-top { margin-top:16px; }
.search-bar {
    position:relative;
    width:70%;
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

/* .input-box:blank ~ .text-over-input {
    display:block;
} */
.theme {
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
    opacity:0.4;
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
    background-color:#596FE5;
    color:white;
}
.selectedSearchType {
    opacity:1 !important;
}
.barUnderWord {
    position:absolute;
    display:none;
    width:44px;
    height:4px;
    background-color:#596FE5;
    bottom:0;
    left:0;
    z-index:-1;
}
.shouldIDisplay {
    display:block !important;
}
</style>