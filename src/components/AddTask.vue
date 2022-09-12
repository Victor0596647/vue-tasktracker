<template>
    <div class="addtask-container">
        <h1>Add a Task</h1>
        
        <form>
            <label>Task Description</label>
            <input type="text" id="task-title" />
            <label>Task Date</label>
            <input type="date" id="task-date" />
            <label>Reminder</label>
            <input type="checkbox" id="task-reminder"/>
            <input type="submit" id="submit-task" />
        </form>
    </div>
</template>

<script>
    export default {
        name: 'AddTask',
        props: {
        },
        data(){
            return {
                display: false
            }
        }
    }
</script>

<style>

</style>