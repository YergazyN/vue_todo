<template>
    <div class="posts_wrap" v-show="posts.length > 0">
      <h3>Posts List</h3>
      <post-item
        
        v-for="post in posts" 
        :post="post"
        v-bind:key="post.id"
        @remove="$emit('remove', post)"
       />
    </div>
    <div class="posts_wrap" v-show="posts.length === 0">
      <h3>Add a Post</h3>
    </div>
</template>

<script>
import PostItem from './PostItem.vue'
export default {
  components: { PostItem },
  name: 'postList',
  props: {
    posts: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped lang="scss">
  .posts_wrap{
    width: 50%;
    margin: 15px;
  }
</style>