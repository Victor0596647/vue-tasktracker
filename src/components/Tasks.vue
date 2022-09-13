<template>
    <div :key="task.id" v-for="task in tasks" class="tasks-container">
        <Task :task="task" @delete-task="$emit('delete-task', task.id)" @toggle-remind="$emit('toggle-remind', task.id)"/>
    </div>
</template>

<script>
    import Task from './Task.vue'

    export default {
        name: 'Tasks',
        props: {
            tasks: Array, 
        },
        components: {
            Task
        }
    }
</script>