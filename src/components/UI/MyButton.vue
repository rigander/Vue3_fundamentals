<template>
    <button>
        <slot></slot>
    </button>
</template>

<script>
export default {
    name: 'my-button'
}
</script>

<style lang="scss" scoped>
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
button:active{
  background-color: #b9b561;
  color: aliceblue;
}
button:hover{
  cursor: pointer;
}
</style>