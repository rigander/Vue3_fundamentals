<template>
    <div>
        <h3 class="title__list-of-users">
            List of users</h3>
    </div>
<post-item
        :post="post"
        v-for="post in posts"
/>
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