<template>
    <form @submit.prevent>
        <input  v-bind:value="post.title"
                @input="post.title = $event.target.value"
                class="input"
                type="text"
                placeholder="Name"
        >
        <br>
        <textarea
                v-bind:value="post.body"
                @input="post.body = $event.target.value"
                class="textarea"
                type="text"
                placeholder="Description"
                rows="10" cols="60"
        ></textarea>
        <br>
        <button
                class="btn"
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
</style>