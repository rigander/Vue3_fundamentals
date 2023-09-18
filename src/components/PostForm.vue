<template>
    <form @submit.prevent>
        <my-input
                v-focus
                v-model="post.title"
                type="text"
                placeholder="Name"
        />
        <br>
        <my-input
                v-model="post.body"
                placeholder="Description"
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
    },
}
</script>

<style scoped>
</style>