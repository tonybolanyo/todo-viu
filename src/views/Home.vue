<template>
<div>
  <AddTask @add-task="addTask" v-show="showAddTask" />
  <Tasks :tasks="tasks" @delete-task="deleteTask"
    @toggle-important="toggleImportant"/>
</div>
</template>

<script>
import Tasks from '../components/Tasks'
import AddTask from '../components/AddTask'

export default {
  name: 'Home',
  components: {
    Tasks,
    AddTask
  },
  props: {
    showAddTask: Boolean
  },
  data () {
    return {
      tasks: []
    }
  },
  methods: {
    async deleteTask (id) {
      const res = await fetch(`http://localhost:3000/tasks/${id}`, {
        method: 'DELETE'
      })

      res.status === 200
        ? (this.tasks = this.tasks.filter(task => task.id !== id))
        : alert('Error eliminando la tarea')
    },
    async toggleImportant (id) {
      const taskToggle = await this.fetchTask(id)
      const updatedTask = { ...taskToggle, important: !taskToggle.important }

      const res = await fetch(`http://localhost:3000/tasks/${id}`, {
        method: 'PUT',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(updatedTask)
      })

      const data = await res.json()
      console.log(data)

      this.tasks = this.tasks.map(
        task => task.id === id ? { ...task, important: !task.important } : task)
    },
    async fetchTask (id) {
      const res = await fetch(`http://localhost:3000/tasks/${id}`)
      const data = await res.json()
      return data
    },
    async fetchAllTasks () {
      const res = await fetch('http://localhost:3000/tasks')
      const data = await res.json()
      return data
    },
    async addTask (task) {
      const res = await fetch('http://localhost:3000/tasks', {
        method: 'POST',
        headers: {
          'Content-type': 'application/json'
        },
        body: JSON.stringify(task)
      })
      const data = await res.json()
      console.log(data)
      this.tasks = [...this.tasks, data]
    }
  },
  async created () {
    this.tasks = await this.fetchAllTasks()
  }
}
</script>
