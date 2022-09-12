<template>
    <div :class="[task.reminder ? 'reminder' : '', 'task-container']" @click="toggleRemind(task.id)">
        <div>
            <h3>{{ task.text }}</h3>
            <p>{{ task.day }}</p>
        </div>
        <i class="bi bi-trash" @click="onDelete(task.id)"></i>
    </div>
</template>

<script>
    export default {
        name: 'Task',
        props: {
            task: Object
        },
        methods: {
            onDelete(id){
                this.$emit('delete-task', id)
            },
            toggleRemind(id){
                this.$emit('toggle-remind', id)
            }
        }
    }
</script>

<style>
    .task-container {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
        background-color: rgb(216, 216, 216);
        border-radius: 5px;
        padding: 1px;
        padding-left: 10px;
        margin-bottom: 10px;
        border-left: 5px rgb(194, 194, 194) solid;
    }
    .bi.bi-trash{
        transform: scale(2);
        width: 30px;
        cursor: pointer;
        transition: 100ms ease-in-out;
    }
    .bi.bi-trash:hover{
        color: aliceblue;
    }
    .task-container.reminder {
        border-left: 5px rgb(24, 24, 24) solid;
    }
</style>