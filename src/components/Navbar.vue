<template>
    <div class="navbar">
      <div class="header"></div>
        <div class="navbar__btns">
            <my-button @click="$router.push('/')">Main</my-button>
            <my-button @click="$router.push('/posts')">Posts</my-button>
            <my-button @click="$router.push('/about')">About</my-button>
            <my-button @click="$router.push('/store')">Store</my-button>
            <my-button @click="$router.push('/composition')">Composition</my-button>
        </div>
    </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
.navbar{
  height: 45px;
  background-color: #b9b561;
  box-shadow: 2px 2px 4px grey;
  display: flex;
  align-items: center;
}
.header{
  padding: 4px;
}
</style>