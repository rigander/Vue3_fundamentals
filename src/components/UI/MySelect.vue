<template>
    <select :value="modelValue" @change="changeOption">
        <option disabled value="">Choose from the list</option>
        <option
                v-for="option in options"
                :key="option.value"
                :value="option.value"
        >
            {{ option.name }}
        </option>
    </select>
</template>

<script>
export default {
    name: 'my-select',
    props: {
        modelValue: {
            type: String
        },
        options: {
            type: Array,
            default: () => []
        }
    },
    methods: {
        changeOption(event) {
            this.$emit('update:modelValue', event.target.value);
        }
    }
}
</script>

<style scoped>
select{
    color: #3c3f41;
    font-weight: bold;
    font-size: 19px;
    height: 50px;
    width: 250px;
    margin: 5px;
    background-color: #b9b561;
    border-radius: 4px;
    border: none;
}
</style>