<template>
    <div class="addtask-container" >
        <form @submit="onSubmit" class="addtask-form">
            <h2>Add a Task</h2>

            <label>Task Description</label>
            <input type="text" id="task-title" v-model="text" />
            <br>
            <label>Task Date</label>
            <input type="date" id="task-date" v-model="date"/>
            <br>
            <div>
                <label>Reminder</label>
                <input type="checkbox" id="task-reminder" v-model="reminder"/>
            </div>
            <br>
            <input type="submit" id="submit-task" value="Create New Task"/>
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
                text: '',
                date: '',
                reminder: false
            }
        },
        methods: {
            onSubmit(e)
            {
                e.preventDefault();
                if(!this.text || !this.date)
                {
                    alert("Please fill in the empty fields");
                    return
                }

                const newTask = {
                    id: Math.floor(Math.random() * 10000),
                    text: this.text,
                    day: this.date,
                    reminder: this.reminder
                }

                this.text = '';
                this.date = '';
                this.reminder = false;
                this.$emit('add-task', newTask);
            }
        }
    }
</script>

<style scoped>
    .addtask-container {
        padding: 10px;
        background-color: whitesmoke;
        height: fit-content;
    }
    .addtask-form {
        display: flex;
        flex-direction: column;
        max-width: 480px;
        margin:auto;
    }

    .addtask-form div {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    #submit-task{
        border-radius: 3px;
        border-width: 0px;
        padding: 10px;
        font-weight: bold;
        color: #f0f8ff;
        cursor: pointer;
        background-color: black;
    }

    #task-title, #task-date {
        border-top: 0;
        border-left: 0;
        border-right: 0;
        background-color: whitesmoke;
    }
</style>