<template>
    <div class="input-group mb-3">
        <input 
            type="text" 
            class="form-control" 
            placeholder="Escribe una tarea" 
            v-model="nuevaTarea" 
            @keyup.enter="addTask"
            :class="{'is-invalid': attempSubmit && missingTask}"
        >
        <span class="input-group-btn">
            <button type="button" class="btn btn-primary" @click="addTask">Agregar</button>
        </span>
    </div>
</template>
<script>
export default {
    props:['tareas'],
    data() {
        return {
            nuevaTarea: '',
            attempSubmit: false,
        }
    },
    computed: {
        missingTask: function(){
            return this.nuevaTarea === '';
        }
    },
    methods: {
        addTask: function(event){
            this.attempSubmit = true;

            if(this.missingTask)
                event.preventDefault();

            var text = this.nuevaTarea.trim();

            if(text.length > 0){
                this.tareas.push(
                    {
                        'texto': this.nuevaTarea,
                        'terminada': false
                    }
                );
            }
            // clear value
            this.nuevaTarea = '';
        }
    }
}
</script>
