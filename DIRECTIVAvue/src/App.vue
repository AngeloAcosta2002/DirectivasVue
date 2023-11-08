<script setup>
import { ref } from 'vue';

let newTask = ref ('')
let taskList = ref([
  {
    name: 'Estudiar',
    done: true,

  },
  {
    name: 'Comer', 
    done: false,
    
  },
  {
    name: 'Dormir',
    done: false,
    
  }
  
])
function setDone(index) {
  taskList.value[index].done = true
}

function addTask() {
  if(newTask.value.trim() === '')return
  taskList.value.push({
    name: newTask.value,
    done: false
  })
  newTask.value = ''
}

</script>

<template>
  <div class="container">
    <h1>Lista de Tarea</h1>
    <p class="subtitle">{{ newtask }}</p>

    <div>
      <div class="task" :class="{done: task.done}" v-for="(task, index) in taskList" :key="index">{{ task.name }}<span @click="setDone(index)" class="button">x</span></div>
      <!-- *<div class="task">Tarea 2 <span class="button">x</span></div> -->
    </div>

    <input v-model="newTask" @keypress.enter="addTask" type="text" placeholder="Escriba su tarea">
    <p v-show="newTask != '' " class="help">Presiona enter para agg la tarea</p>
  </div>
  
</template>

<style scoped>
.container {
  padding: 6px 12px;
  font-family: "Edu TAS Beginner", cursive;
  background-color: #00747C;
  border-radius: 8px;
  max-width: 420px;
  margin: 0 auto;
  padding: 6px 12px;
}

.done{
  text-decoration: line-through;
}
.help{
  font-size: 8px;
  opacity: 0.6;
  margin: 0;
}
.button{
  background-color: #878787;
  display: inline-block;
  padding: 0 8px;
  border-radius: 6px;
}

.button:hover{
  cursor: pointer;
}

input{
  border: none;
  border-radius: 4px;
  padding: 2px 6px;
  outline: none;
  box-sizing: border-box;
  width: 100%;
  margin-top: 12px;
}

input::placeholder{
  opacity: 0.4;  
}
.task:hover {
  background-color: rgba(32, 32, 34, 0.7);
}

.subtitle {
  font-size: 10px;
  margin: 0;
  margin-bottom: 20px;
  text-align: center;
  opacity: 0.6;
}

h1{
  text-transform: uppercase;
  font-size:  18px;
  text-align: center;
  margin: 0;
  margin-top: 12px;
}

.task {
  display: flex;
  justify-content: space-between;
  background-color: #CACACA;
  border-radius: 4px;
  margin-bottom: 8px;
  padding: 2px 2px 1px 6px;
}

</style>
