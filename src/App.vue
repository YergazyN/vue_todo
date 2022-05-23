<template>
  <div>
    <div class="top">
      <h1>Posts Page</h1>
      <my-button
        @click="showDialog"
        >Add Post
      </my-button>

      <my-button
        @click="fetchPosts"
        >Get Posts
      </my-button>
    </div>
    


    <my-dialog v-model:show="dialogVisible">
      <PostForm  @add="addPost" />
    </my-dialog>
    
    <PostList 
    :posts="posts"
    @remove="removePost"
    v-if="!isPostsLoading"   
    />

    <div v-else class="preloader">Loading ...</div>
    
  </div>
</template>



<script>

  import PostForm from './components/PostForm.vue';
  import PostList from './components/PostList.vue';
  import MyDialog from './components/UI/MyDialog.vue';
  import axios from "axios";

  export default{
    components: {
      PostList, PostForm,
        MyDialog
    },
    data() {
      return {
        posts: [],
        dialogVisible: false,
        isPostsLoading: false
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
      },
      async fetchPosts() {        
        try {
          this.isPostsLoading = true;
          setTimeout(async () => {
            const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
            console.log(response);
            this.posts = response.data;
            this.isPostsLoading = false;
          }, 2000) 
          
        } catch {
          alert("Error")
        } finally{
          
        }
      }     
    },

    // hooks outside of methods
    mounted() {
        console.log('mounted');
        this.fetchPosts();
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

.preloader{
  padding: 15px;
}


</style>
