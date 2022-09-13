<template>
  <div class="container">
    <Header title='Task Tracker' :showAddTask="showAddTask" @toggle-add-task="toggleAddTask"/>
    <AddTask @add-task="addTask" v-show="showAddTask"/>
    <Tasks 
      @delete-task="deleteTask" 
      @toggle-remind="toggleReminder" 
      :tasks="tasks"
    />
  </div>
</template>

<script>
  import Header from './components/Header.vue'
  import Tasks from './components/Tasks.vue'
  import AddTask from './components/AddTask.vue'

  export default {
    name: 'App',
    components: {
      Header,
      Tasks,
      AddTask
    },
    data() {
      return {
        tasks: [],
        showAddTask: false
      }
    },
    created() {
      this.tasks = [
        
      ]
    },
    methods: {
      deleteTask(id) {
        if(confirm("Remove this task?"))
        {
          this.tasks = this.tasks.filter((task) => task.id != id)
          //console.log(this.tasks)
        }
      },
      toggleReminder(id) {
        this.tasks = this.tasks.map((task) => task.id == id ? {...task, reminder: !task.reminder} : task)
      },
      addTask(task)
      {
        this.tasks = [...this.tasks, task];
        this.showAddTask = false;
      },
      toggleAddTask()
      {
        this.showAddTask = !this.showAddTask;
      }
    }
  }
</script>