<template>
  <header>
    <h1>TODO VIU APP</h1>
    <Button :text="showAddTask ? 'Cerrar' : 'Agregar tarea'"
      :color="showAddTask ? '#B00' : 'green'"
      @btn-click="$emit('toggle-add-task')"
      />
  </header>
</template>

<script>
import Button from './Button'

export default {
  name: 'Header',
  components: {
    Button
  },
  props: {
    showAddTask: Boolean
  }
}
</script>

<style scoped>
  header {
    margin-bottom: 30px;
  }
</style>
