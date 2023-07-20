<template>
    <div
        v-if="posts.length > 0"
    >
        <h3 class="title__list-of-users">
            Posts list</h3>
        <post-item
            v-for="post in posts"
            :post="post"
            :key="post.id"
            @remove="$emit('remove', post)"
        />
    </div>
    <h2
        v-else
        style="color: red">Post list is empty</h2>
</template>

<script>
import PostItem from "@/components/PostItem.vue";

export default {
    name: "PostList",
    components: {PostItem},
    props: {
        posts: {
            type: Array,
            required: true
        }

    }
}
</script>

<style scoped>
.title__list-of-users{
    margin: 15px;
    color: chocolate;
}
</style>