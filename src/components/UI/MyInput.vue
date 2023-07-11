<template>
    <input
            :value="modelValue"
            @input="updateInput"
            class="input"
            type="text">
</template>

<script>
export default {
    name: 'my-input',
    props: {
        modelValue: [String, Number]
    },
    methods: {
        updateInput(event){
            this.$emit('update:modelValue', event.target.value)
        }
    }
}
</script>

<style lang="scss" scoped>
.input{
  margin: 10px;
  padding: 5px;
  width: 490px;
  height: 25px;
  background-color: #bbb666;
  border: none;
  border-radius: 2px;
}
</style>