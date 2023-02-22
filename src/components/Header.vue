<script setup>

</script>

<template>
    <div>
        <div class="flex justify-center align-center small-padding-top">
        
            <div class="search-bar">
                <img src="../assets/search.svg">
                
                <input v-model="searchValue" class="input-box" id="search" type="text" placeholder="Search">
            </div>
            <div @click="lightTheme=!lightTheme; sendThemeStatus(lightTheme);" class="theme">
                <img v-if="lightTheme" src="../assets/moon.png">
                <img v-if="!lightTheme" src="../assets/sun.png">
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
            lightTheme:true,
            searchValue:"",
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
        sendThemeStatus(bool) {
            this.$emit('changeThemeStatus', bool)
        }
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
    background-color:#596FE5;
    color:white;
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