<template>
    <button :style="{background: color}" @click="onClick" >{{ text }}</button>
</template>

<script>
    export default {
        name: 'Button',
        props: {
            text: String,
            color: String
        },
        methods: {
            onClick()
            {
                this.$emit('btn-click');
            }
        }
    }
</script>

<style scoped>
    button {
        border-radius: 3px;
        border-width: 0px;
        padding: 10px;
        font-weight: bold;
        color: aliceblue;
        cursor: pointer;
    }
</style>