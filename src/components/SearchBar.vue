<template>
    <div>
        <input @keypress="onKeypress"/><!-- @input="onInput"-->
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
        },
        onKeypress: function(event) {
            if (event.keyCode === 13) {
                this.$emit(
                    'termChange', 
                    event.target.value
                );
            }
        }
    }
};
</script>

<style scoped>
    input {
        width: 75%;
    }

    div {
        text-align: center;
        margin: 20px;;
    }
</style>