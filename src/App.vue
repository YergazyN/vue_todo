<template>
  <div>
    <div class="top">
      <h1>Posts Page</h1>
      <my-button
        @click="showDialog"
        >Add Post
      </my-button>
    </div>
    


    <my-dialog v-model:show="dialogVisible">
      <PostForm  @add="addPost" />
    </my-dialog>
    
    <PostList 
    :posts="posts"
    @remove="removePost"   
    />
    
  </div>
</template>



<script>

  import PostForm from './components/PostForm.vue';
  import PostList from './components/PostList.vue';
import MyDialog from './components/UI/MyDialog.vue';

  export default{
    components: {
      PostList, PostForm,
        MyDialog
    },
    data() {
      return {
        posts: [
          {id:1, title: "Post One", text: "Post One Text", author: "Johnny Depp"},
          {id:2, title: "Post Two", text: "Post Two Text", author: "Tom Hanks"},
          {id:3, title: "Post Three", text: "Post Three Text", author: "Brad Pitt"},
          {id:4, title: "Post Four", text: "Post Four Text", author: "Robert Downey Jr."},
          {id:5, title: "Post Five", text: "Post Five Text", author: "Emma Watson"}
        ],
        dialogVisible: false
      }
    },

    methods: {
      addPost(post) {
        this.posts.push(post);
        this.dialogVisible = false;
      },
      removePost(post) {
        this.posts = this.posts.filter(p => p.id !== post.id)
      },

      showDialog() {
        this.dialogVisible = true
      }
      
    }
  }
</script>

<style lang="scss">

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.top{
  padding: 15px;

  button{
    margin-top: 15px;
  }
}


</style>
