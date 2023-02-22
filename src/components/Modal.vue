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
        <div class="used-area flex flex-col">

            <div class="img-wrapper relative">
                <img :src="articleImage">

                <div class="title">
                    {{ articleTitle }}
                </div>
            </div>



            <div class="content">
                {{fixed_content}}
                <span class="article-link">
                    <a :href="articleLink" target="_blank">{{ articleAuthor }}</a>
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
    computed: {
        fixed_content() {
            let firstBracketIndex = this.articleContent.lastIndexOf("[");
            let secondBracketIndex = this.articleContent.lastIndexOf("]");
            let firstPartOfContent = this.articleContent.substring(0, firstBracketIndex);
            let secondPartOfContent = this.articleContent.substring(secondBracketIndex, this.articleContent.length - 1)
            return firstPartOfContent + secondPartOfContent;
        }
    }
}
</script>

<style scoped>
.title {
    position:absolute;
    bottom:3px;
    left:0;
    right:0;
    color:white;
    background-color:rgba(0, 0, 0, 0.521);
    font-size:18px;
    padding-left:10px;
    padding-right:10px;
    padding-bottom:3px;
    padding-top:5px;
}
.content {
    padding-left:20px;
    padding-right:20px;
    padding-bottom:6px;
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
    z-index: 10;
}
.img-wrapper {
    max-width:100%;
    /* max-height:300px; */
}
.img-wrapper img {
    height:100%;
    width:100%;
    object-fit: cover;
}

</style>