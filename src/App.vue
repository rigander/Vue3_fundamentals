<template>
  <div class="app">
  <post-form/>
  <post-list :posts="posts"/>
  </div>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
export default {
    components: {
      PostList, PostForm
    },
    data() {
        return {
           posts: [
               {id: 1, title: 'JavaScript', body: 'JS Description'},
               {id: 2, title: 'Python', body: 'Python Description'},
               {id: 3, title: 'Java', body: 'Java Description'},
               {id: 4, title: 'C++', body: 'C++ Description'},
           ],
            title: '',
            body: '',
        }
    },
    methods: {
        createPost() {
            const newPost = {
               id: Date.now(),
               title: this.title,
               body: this.body,
            }
            this.posts.push(newPost);
            this.title = '';
            this.body = '';
        },
        inputTitle(event){
            this.title = event.target.value;
        },
        inputBody(event){
            this.body = event.target.value;
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