<template>
    <form @submit.prevent>
        <my-input
                v-model="post.title"
                type="text"
                placeholder="Name"
        />
        <br>
        <my-input
                v-model="post.body"
                placeholder="Description"
                rows="10" cols="60"
        />
        <br>
        <my-button
                class="btn"
                @click="createPost"
        >Create</my-button>
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