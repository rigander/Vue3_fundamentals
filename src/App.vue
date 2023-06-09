<template>
  <div>
      <div>
          <button @click="addLike">Like</button>
          <button @click="addDislike">Dislike</button>
          <hr>
      </div>
      <div>Number of Likes: <strong>{{ likes }}</strong></div>
      <div>Number of Dislikes: <strong>{{ dislikes }}</strong></div>
  </div>
</template>

<script>
export default {
    data() {
        return {
           likes: 0,
           dislikes: 0,
        }
    },
    methods: {
      addLike(){
          this.likes += 1;
      },
      addDislike(){
          this.dislikes +=1;
      }
    }
}
</script>

<style>
body{
    background-color: #3c3f41;
    color: aliceblue;
    font-size: 30px;
}
textarea{
    background-color: aliceblue;
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
</style>