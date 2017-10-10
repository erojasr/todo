<template>
 <div>  
<ul class="list-group mb-3">
    <li class="list-group-item" v-for="(tarea,index) in tareas" :class="{ 'list-group-item-danger' : tarea.terminada}">
        {{tarea.texto}}
        <span class="float-right">
            <button 
                type="button" 
                class="btn btn-success btn-xs fa fa-check"
                @click="tarea.terminada = !tarea.terminada"
            ></button>
            <button 
            type="button" 
            class="btn btn-danger btn-xs fa fa-times"
            @click="deleteTask(index)"
            ></button>
        </span>
    </li>
</ul>

<div class="card" style="width: 20rem;" v-if="tareas.length > 0">
    <ul class="list-group list-group-flush">
        <li class="list-group-item">Done Task: {{ taskAlreadyDone }}</li>
        <li class="list-group-item">Pending Task: {{ taskNotFinishYet }}</li>
    </ul>
</div>


</div>

</template>
<script>
export default {
  props:['tareas'],
  data(){
      return {
        doneTask: 0,
        pendingTask: 0
      }
  },
  computed: {
    taskAlreadyDone: function(){
        
        var completed = [];
        this.tareas.forEach(function(value, key) {
            if(value.terminada)
                completed.push(key);
        }, this);

        var result = Math.round(completed.length * 100) / this.tareas.length;
        return this.doneTask = result.toFixed(1);
    },
    taskNotFinishYet: function(){
        var pending = [];
        this.tareas.forEach(function(value, key) {
            if(!value.terminada)
                pending.push(key);
        }, this);

        var result = Math.round(pending.length * 100) / this.tareas.length;
        return this.pendingTask = result.toFixed(1);
    }
  },
  methods:{
    deleteTask: function(index){
        this.tareas.splice(index,1);
    }
  }
}
</script>
