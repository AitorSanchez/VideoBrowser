<template>
    <div>
        <input/><!-- @input="onInput"-->
        <button class="btn btn-primary" @click="onInput">Search</button>
    </div>
</template>

<script>
export default {
    name: 'SearchBar',
    methods: {
        onInput: function(event) {
            this.$emit(
                'termChange', 
                event.target.previousElementSibling.value
            );
        }
    }
};
</script>

<style>

</style>