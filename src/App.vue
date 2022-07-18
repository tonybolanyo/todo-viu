<template>
  <div class="container">
    <Header :showAddTask="showAddTask" @toggle-add-task="onToggleAddTask"/>
    <router-view :showAddTask="showAddTask"></router-view>
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header'
import Footer from './components/Footer'

export default {
  name: 'App',
  components: {
    Header,
    Footer
  },
  data () {
    return {
      showAddTask: false
    }
  },
  methods: {
    onToggleAddTask () {
      this.showAddTask = !this.showAddTask
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,400;1,300&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Poppins, Arial, Helvetica, sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  min-height: 300px;
  border: solid thin steelblue;
  padding: 30px;
}

.btn {
  display: inline-block;
  padding: 10px 20px;
  border-radius: 5px;
  border: none;
  cursor: pointer;
  background-color: blue;
  color: white;
  font-weight: bold;
  font-size: 15px;
}
</style>
