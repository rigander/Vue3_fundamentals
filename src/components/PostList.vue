<template>
    <div
        v-if="posts.length > 0"
    >
        <h3 class="title__list-of-users">
            Posts list</h3>
        <transition-group name="list">
            <post-item
                v-for="post in posts"
                :post="post"
                :key="post.id"
                @remove="$emit('remove', post)"
            />
        </transition-group>
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
.list-item {
    display: inline-block;
    margin-right: 10px;
}
.list-enter-active,
.list-leave-active {
    transition: all 0.3s ease;
}
.list-enter-from,
.list-leave-to {
    opacity: 0;
    transform: translateX(130px);
}
.list-move {
    transition: transform 0.5s ease;
}
.title__list-of-users{
    margin: 15px;
    color: chocolate;
}
</style>