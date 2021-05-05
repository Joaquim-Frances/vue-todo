<template>
    <div id="addContainer">
        <form @submit="addTodo">
            <input type="text" v-model="title" placeholder="Añade una tarea...">
        </form>
    </div>
</template>

<script>
import {uuid} from 'vue-uuid';
export default {
    name: 'TodoAdd',
    data() {
        return {
            title:'',
        }
    },
    methods: {
        addTodo(e){
            e.preventDefault();
            const newTodo = {
                id: uuid.v4(),
                title: this.title,
                completed: false,
            };

            this.title='';
            this.$emit('addTodo', newTodo);
        }
    },
    
}
</script>

<style scoped>
   #addContainer{
        height: 70px;
    }

    form{
        display: flex; 
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 70px;
        width: 100%;
    }

    input{
        
        padding: 10px;
        outline: none;
        border: solid 1px #ccc;
        border-radius: 7px;
        width: 90%;
    }
</style>