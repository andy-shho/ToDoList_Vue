<script setup lang="ts">
import { ref, provide } from 'vue'

let id = 0

const newTask = ref('')
const todos = ref([])

const emit = defineEmits(['response'])



const addToDo = () => {
  emit('response', newTask.value)
  newTask.value = ''

}


</script>

<template>
  <div class="about">
    <h1>Add Tasks to To Do List</h1>
    <form id="add" @submit.prevent="addToDo">
        <input v-model="newTask" required placeholder="Enter new task">
        <button>Add Task</button>
    </form>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
  }
  #add{
    margin: 10 10 10 10;
  }
}
</style>
