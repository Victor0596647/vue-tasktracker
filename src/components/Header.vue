<template>
    <header>
        <h1>{{ title }}</h1>
        <Button text='Add task' color='black' @click="addTask()"/>
    </header>
</template>

<script>
    import Button from './Button.vue' 

    export default {
        name: 'Header',
        props: {
            title: String,
        },
        components: {
            Button
        },
        methods: {
            addTask(){
                alert("hello you clicked!")
            }
        }
    }
</script>

<style scoped>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
</style>