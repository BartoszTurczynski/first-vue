<template>
<div class="container">
<Header @toggle-add-task="toggleAddTask" title="Task Tracker" :showAddTask="showAddTask"/>
<div v-if="showAddTask">
<AddTask @add-task="addTask" />
</div>
<Tasks @toggleReminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
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
  methods: {
    toggleAddTask () {
      this.showAddTask = !this.showAddTask
    },
    toggleReminder (id) {
      this.tasks = this.tasks.map(
        task => task.id === id ? { ...task, reminder: !task.reminder } : task)
    },
    deleteTask (id) {
      if (confirm('Are you sure?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    addTask (task) {
      this.tasks = [...this.tasks, task]
    }
  },
  data () {
    return {
      tasks: [],
      showAddTask: false
    }
  },
  created () {
    this.tasks = [
      {
        id: 1,
        text: 'Meeting at school',
        day: 'March 3rd at 1:30pm',
        reminder: true
      },
      {
        id: 2,
        text: 'Food shoping',
        day: 'March 3rd at 11:00am',
        reminder: false
      },
      {
        id: 3,
        text: 'Doctors appointment',
        day: 'March 1st at 2:30pm',
        reminder: true
      }
    ]
  }
}
</script>

<style>
body {
  font-size: 110%;
  border : 2px solid lightgreen;
  border-radius: 5px;
  padding: 1%;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  }
</style>
