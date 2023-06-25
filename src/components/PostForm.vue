<template>
    <form @submit.prevent>
        <input
                v-model="post.title"
                class="input"
                type="text"
                placeholder="Name"
        >
        <br>
        <textarea
                v-model="post.body"
                class="textarea"
                placeholder="Description"
                rows="10" cols="60"
        ></textarea>
        <br>
        <button
                class="btn"
                @click="createPost"
        >Create</button>
    </form>
</template>

<script>
export default {
    name: "PostForm",
    data(){
        return {
            post:{
                title: '',
                body: ''
            }
        }
    },
    methods: {
        createPost() {
            this.post.id = Date.now();
            this.$emit('create', this.post)
            this.post = {
                title: '',
                body: ''
            }
        }
    }
}
</script>

<style scoped>
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
button:active{
    background-color: #b9b561;
    color: aliceblue;
}
button:hover{
    cursor: pointer;
}
</style>