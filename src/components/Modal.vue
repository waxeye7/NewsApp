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
    {{ articleTitle }}
</template>

<script>
export default {
    data() {

    },
}
</script>

<style scoped>

</style>