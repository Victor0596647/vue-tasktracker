<template>
    <header>
        <h1>{{ title }}</h1>
        <Button :text="showAddTask ? 'Close' : 'Add task'" color="black" @click="$emit('toggle-add-task')" />
    </header>
</template>

<script>
    import Button from './Button.vue' 
    import AddTask from './AddTask.vue'

    export default {
        name: 'Header',
        props: {
            title: String,
            showAddTask: Boolean
        },
        components: {
            Button,
            AddTask
        },
        methods: {
            
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