<script setup>
import Modal from "./Modal.vue";

defineProps({ 
    articleObject: {
    type: Object,
    required: true
  }
});
</script>

<template>
    <Modal :article-title="articleObject.title" />

    <div class="container">

        <div class="flex">

            <div class="img-wrapper">
                <img :src="articleObject.urlToImage">
            </div>


            <div class="text">
                <div class="title">{{articleObject.title}}</div>
                &nbsp;
                <div class="description">{{articleObject.description.split(" ").slice(0,40).join(" ")}}</div>
            </div>

        </div>

    </div>
    
</template>

<script>
export default {
    data() {

    },
}
</script>

<style scoped>
.img-wrapper {
    min-height:84px;
    max-height:140px;
    min-width:110px;
    max-width:110px;
    border-radius:12px 0 0 12px;

    overflow:hidden;
}
.img-wrapper img {
    height:100%;
    width:100%;
    object-fit:cover;
    object-position:center;
}
.container {
    background-color:#ECECEC;
    border-radius:12px;
    margin-left:20px;
    margin-right:20px;
    margin-top:8px;
    max-height:140px;
    overflow: hidden;
}
.text {
    padding:8px 8px 8px 8px;
}
.title {
    display: inline;
    font-size:15px;
    margin-bottom:0px;
}
.description {
    display:inline;
    font-size:12px;
}
</style>