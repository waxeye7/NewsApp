<script setup>
defineProps({
    articleTitle: {
        type:String,
        required:true
    },
    articleContent: {
        type: String,
        required: true
    },
    articleImage: {
        type:URL,
        required:true
    },
    articleLink: {
        type:URL,
        required:true
    }
});
</script>

<template>
    <div class="modal">
        <div class="img-wrapper">
            <img :src="articleImage">
        </div>
        {{ articleTitle }}
        {{ articleContent }}
        {{ articleLink }}
    </div>

</template>

<script>
export default {
    data() {

    },
}
</script>

<style scoped>
.modal {
    position:fixed;
    top:0;
    bottom:0;
    left:0;
    right:0;
    height:100%;
}
.img-wrapper {
    max-width:100%;
    max-height:400px;
}
.img-wrapper img {
    height:100%;
    width:100%;
}

</style>