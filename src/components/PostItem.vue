<template>
    <div class="post">
        <div>
            <div><strong>Title:</strong> {{ post.title }}</div>
            <div><strong>Body:</strong> {{ post.body }}</div>
            <div><strong>Id:</strong> {{ post.id }}</div>
        </div>
        <div class="post__btns">            
            <my-button
                @click="$emit('remove', post)"
            >
                Delete
            </my-button>
        </div>
    </div>
</template>
<script>

import MyButton from "./UI/MyButton.vue"
export default {
    components: {
        MyButton
    },
    props: {
       post: {
           type: Object,
           required: true
       } 
    }
}
</script>
<style lang="scss">
    .post{
        padding: 15px;
        border: 2px solid teal;
        margin-top: 15px;
        display: flex;
        align-items: center;
        justify-content: space-between;;
    }

    .post__btns{
        margin-left: 20px;
    }
</style>