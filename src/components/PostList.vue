<template>
    <div class="post" v-for="post in posts">
        <div><strong>Name: </strong>{{post.title}}</div>
        <div><strong>Description: </strong>{{post.body}}</div>
        <div><strong>Id: </strong>{{post.id}}</div>
    </div>
</template>

<script>
export default {
    name: "PostList",
    props: {
        posts: {
            type: Array,
            required: true
        }

    }
}
</script>

<style scoped>
.post{
    margin-top: 15px;
    background-color: #2b2b2b;
    padding: 15px;
    border: 3px solid darkkhaki;
    border-radius: 3px;
}
</style>