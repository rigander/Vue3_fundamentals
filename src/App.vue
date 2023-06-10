<template>
  <div>
      <div>
          <form @submit.prevent>
              <input  v-bind:value="title"
                      @input="title = $event.target.value"
                      class="input"
                      type="text"
                      placeholder="Name"
              >
              <br>
              <textarea
                      v-bind:value="body"
                      @input="body = $event.target.value"
                      class="textarea"
                      type="text"
                      placeholder="Description"
                      rows="10" cols="60"
              ></textarea>
              <br>
              <button
                  class="btn"
                  @click="createPost"
              >Create</button>
          </form>
      </div>
     <div class="post" v-for="post in posts">
         <div><strong>Name: </strong>{{post.title}}</div>
         <div><strong>Description: </strong>{{post.body}}</div>
         <div><strong>Id: </strong>{{post.id}}</div>
     </div>
  </div>
</template>

<script>
export default {
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
.post{
    margin-top: 15px;
    background-color: #2b2b2b;
    padding: 15px;
    border: 3px solid darkkhaki;
    border-radius: 3px;
}
button{
    margin: 10px;
    width: 100px;
    height: 25px;
    color: chocolate;
    font-size: 15px;
    font-weight: bold;
    border-radius: 3px;
    border: none;
}
input{
    margin: 10px;
    padding: 5px;
    width: 490px;
    height: 25px;
    background-color: #bbb666;
    border: none;
    border-radius: 2px;
}
textarea{
    margin: 10px;
    padding: 5px;
    resize: none;
    font-size: 14px;
    background-color: #bbb666;
    border: none;
    border-radius: 2px;
}
</style>