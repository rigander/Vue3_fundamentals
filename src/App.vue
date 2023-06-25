<template>
  <div class="app">
  <post-form
          @create="createPost"
  />
  <post-list
          :posts="posts"
  />
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
               {id: 5, title: 'TS', body: 'TS Description'},
           ],
        }
    },
    methods: {
        createPost(post){
            this.posts.push(post);
        },
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