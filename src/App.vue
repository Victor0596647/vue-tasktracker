<template>
  <div class="container">
    <Header title='Task Tracker'/>
    <Tasks :tasks="tasks" @delete-task="deleteTask" @toggle-remind="toggleReminder" />
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
        tasks: []
      }
    },
    methods: {
      deleteTask(id) {
        if(confirm("Remove this task?"))
        {
          this.tasks = this.tasks.filter((task) => task.id != id)
          console.log(this.tasks)
        }
      },
      toggleReminder(id) {
        this.tasks = this.tasks.map((task) => task.id == id ? {...task, reminder: !task.reminder} : task)
      }
    },
    created() {
      this.tasks = [
        {
          id : 1,
          text : 'Start a Programming Journey',
          day : 'September 12, 2022',
          reminder : true
        },
        {
          id : 2,
          text : 'Star Wars Day',
          day : 'May 4, 2022',
          reminder : false
        },
        {
          id : 3,
          text : 'Go to Church',
          day : 'October 29, 2022',
          reminder : true
        },
        {
          id : 4,
          text : 'Back-To-School',
          day : 'January 5, 2022',
          reminder : true
        }
      ]
    }
  }
</script>