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
        type:String,
        required:true
    },
    articleLink: {
        type:String,
        required:true
    },
    articleAuthor: {
        type:String,
        required:true
    }
});
</script>

<template>
    <div class="modal">
        <div class="used-area">

                <div class="img-wrapper relative">
                    <img :src="articleImage">

                    <div class="title">
                        {{ articleTitle }}
                    </div>
                </div>



            <div class="content">
                {{ articleContent }}
                <span class="article-link">
                    <a :href="articleLink">{{ articleAuthor }}</a>
                </span>
            </div>

            
        </div>

    </div>

</template>

<script>
export default {
    data() {
        return {

        }

    },
}
</script>

<style scoped>
.title {
    position:absolute;
    bottom:5px;
    left:0;
    right:0;
    color:white;
    background-color:rgba(0, 0, 0, 0.521);
    font-size:18px;
    padding-left:10px;
    padding-right:10px;
}
.content {
    padding-left:10px;
    padding-right:10px;
}
.used-area {
    background-color:rgb(245, 245, 245);
}
.modal {
    position:fixed;
    top:0;
    bottom:0;
    left:0;
    right:0;
    height:100%;
    z-index: 2;
}
.img-wrapper {
    max-width:100%;
    max-height:300px;
}
.img-wrapper img {
    height:100%;
    width:100%;
}

</style>