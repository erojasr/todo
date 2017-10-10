<template>
  <div id="app" class="container">
    <div class="jumbotron">
      <titulo :titulo="titulo"></titulo>
      <new-task :tareas="tareas"></new-task>
      <view-tasks :tareas="tareas"></view-tasks>
    </div>
  </div>
</template>

<script>
import Titulo from './components/Titulo.vue'
import NewTask from './components/NewTask.vue'
import ViewTasks from './components/ViewTasks.vue'
export default {
  components: {
    Titulo,
    NewTask,
    ViewTasks
  },
  data () {
    return {
      titulo: 'Lista de Tareas.',
      tareas: [
        {
            texto: 'Aprender vue.js',
            terminada: false
        },
        {
            texto: 'Aprender Angular 2',
            terminada: false
        },
        {
            texto: 'Aprender C#',
            terminada: true
        }
      ]
    }
  }
}
</script>

<style>

</style>
