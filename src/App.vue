<template>
  <div class="app">
   <h1>Posts Page</h1>
   <my-button
           @click="showDialog"
   >Create Post
   </my-button>
   <my-dialog
           v-model:show="dialogVisible"
   >
      <post-form
              @create="createPost"
      />
   </my-dialog>
  <post-list
          :posts="posts"
          @remove="removePost"
  />
  </div>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyButton from "@/components/UI/MyButton.vue";
export default {
    components: {
        MyButton,
      PostList, PostForm
    },
    data() {
        return {
           posts: [
               {id: 1, title: 'JavaScript', body: 'JS Description'},
               {id: 2, title: 'Python', body: 'Python Description'},
               {id: 3, title: 'Java', body: 'Java Description'},
               {id: 4, title: 'C++', body: 'C++ Description'},
               {id: 5, title: 'TS', body: 'TS Description'},
           ],
            dialogVisible: false,
        }
    },
    methods: {
        createPost(post){
            this.posts.push(post);
            this.dialogVisible = false;
        },
        removePost(post) {
            this.posts = this.posts.filter(p => p.id !== post.id)
        },
        showDialog(){
            this.dialogVisible = true;
        }
    }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
body{
    background-color: #3c3f41;
    color: aliceblue;
    font-size: 30px;
}
</style>