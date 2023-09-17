<template>
    <div>
<h1>Welcome to Vue3</h1>
        <router-link class="links" to="/posts">Posts</router-link>
        <router-link class="links" to="/about">About</router-link>
    </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
.links{
    color: #b9b561;
    padding: 20px;
}
</style>