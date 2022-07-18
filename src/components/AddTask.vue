<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label for="">Tarea</label>
      <input type="text" name="text" id="text" v-model="text">
    </div>
    <div class="form-control">
      <label for="">Día</label>
      <input type="text" name="day" id="day" v-model="day">
    </div>
    <div class="form-control form-control-check">
      <label for="important">Marcar como importante</label>
      <input type="checkbox" name="important" id="important" v-model="important">
    </div>
    <input type="submit" value="Guardar tarea" class="btn">
  </form>
</template>

<script>
export default {
  name: 'AddTask',
  data () {
    return {
      text: '',
      day: '',
      important: false
    }
  },
  methods: {
    onSubmit (event) {
      event.preventDefault()

      if (!this.text) {
        alert('Debes escribir el texto de la tarea')
        return
      }

      const newTask = {
        id: Math.floor(Math.random() * 100000),
        text: this.text,
        day: this.day,
        important: this.important
      }

      this.$emit('add-task', newTask)

      this.text = ''
      this.day = ''
      this.important = false
    }
  }
}
</script>

<style scoped>
  .add-form {
    margin-bottom: 30px;
  }

  .form-control {
    margin: 20px 0;
  }

  .form-control label {
    display: block;
  }

  .form-control input[type=text] {
    width: 100%;
    height: 40px;
    padding: 3px 7px;
    font-size: 17px;
  }

  .form-control-check {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .form-control-check label {
    flex: 1;
  }

  .form-control-check input {
    flex: 1;
    height: 20px;
  }

</style>
