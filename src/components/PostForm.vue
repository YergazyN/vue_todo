<template>
  <div class="add_post">
    <h2>Add Post</h2>
    <form @submit.prevent>
      <my-input          
          v-model="post.title"          
          type="text"
          placeholder="Post title"
      />
      <my-input  
          v-model="post.body"
          type="text"
          placeholder="Post text"
      />
      <my-input
          v-model="post.author"
          type="text"
          placeholder="Author"
      />
      <my-button 
        class="form-item form-button" 
        @click="addPost"
        style="align-self: flex-end"
        >
        Add
        </my-button>
    </form>
  </div>
</template>

<script>
import MyButton from "./UI/MyButton.vue"
export default {
  name: "postForm",
  components: { MyButton },
  data() {
    return {
      post: {
        title: '',
        body: '',
        author: ''
      }
    }
  },

  methods: {

    addPost() {     
        
        this.post.id = Date.now();       
        
        this.$emit('add', this.post);

        this.post = {
          title: '',
          body: '',
          author: ''
        }       
      }
  }
    
}
</script>

<style scoped lang="scss">
  .add_post{
    padding: 15px;
    border: 2px solid teal;
    margin: 0 auto;
    width: 90%;
  
    h2{
      margin-bottom: 25px;
    }
    form{
      display: flex;
      flex-direction: column;        
      
    }
}
</style>