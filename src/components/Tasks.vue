<template>
<div>
  <div :key="task.id" v-for="task in tasks">
    <Task :task="task" @delete-task="$emit('delete-task', task.id)"
      @toggle-important="$emit('toggle-important', task.id)"/>
  </div>
</div>
</template>

<script>
import Task from './Task.vue'
export default {
  name: 'Tasks',
  props: {
    tasks: Array
  },
  components: {
    Task
  }
}
</script>
