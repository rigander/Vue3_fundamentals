<template>
    <div class="post" >
        <div>
            <div><strong>Name: </strong>{{post.title}}</div>
            <div><strong>Description: </strong>{{post.body}}</div>
            <div><strong>Id: </strong>{{post.id}}</div>
        </div>
        <div class="post__btns">
            <my-button

            >Delete</my-button>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        post: {
           type: Object,
           required:  true
        }
    }
}
</script>

<style lang="scss" scoped>
.post{
    margin: 15px;
    background-color: #2b2b2b;
    padding: 15px;
    border: 3px solid darkkhaki;
    border-radius: 3px;
}
</style>