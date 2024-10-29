<script setup lang="ts">
import { toEditorSettings } from 'typescript';
import TheWelcome from '../components/TheWelcome.vue'
import {ref, computed} from 'vue'

const hide = ref(false)
const props = defineProps ({
  tasks: Array
})

const emit = defineEmits(['delete'])

const deleteToDo = (e) =>{
  emit('delete', e)
}

const filteredTodos = computed(() => {
  return hide.value
    ? props.tasks.filter((todo) => !todo.done)
    : props.tasks
})

</script>

<template>
  <main>
    <ul v-if="tasks.length > 0">
      <li v-for="todo in filteredTodos" :key = "todo.id">
        <input type="checkbox" v-model="todo.done">
        <span>{{ todo.text }}</span>
        <span>{{ todo.date }}</span>
        <button @click="deleteToDo(todo)">X</button>
      </li>
    </ul>
    <h1 v-else>
      No Tasks Remaining
    </h1>
    <button @click = "hide = !hide">
      {{ hide ? 'Show all' : 'Hide Completed' }}
    </button>
    <TheWelcome />
  </main>
</template>
