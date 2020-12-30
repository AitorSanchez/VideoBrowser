<template>
    <div>
        <input/><!-- @input="onInput"-->
        <button @click="onInput">Search</button>
    </div>
</template>

<script>
export default {
    name: 'SearchBar',
    methods: {
        onInput: function(event) {
            this.$emit(
                'termChange', 
                event.target.value
            );
        }
    }
};
</script>

<style>

</style>