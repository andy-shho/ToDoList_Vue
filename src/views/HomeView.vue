<script setup lang="ts">
import TheWelcome from '../components/TheWelcome.vue'

const props = defineProps ({
  tasks: Array
})

</script>

<template>
  <main>
    <ul v-if="tasks.length > 0">
      <li v-for="todo in props.tasks" :key = "todo.id">
        <input type="checkbox" v-model="todo.done">
        <span>{{ todo.text }}</span>
        <span>{{ todo.date }}</span>
      </li>
    </ul>
    <h1 v-else>
      No Tasks Remaining
    </h1>
    <TheWelcome />
  </main>
</template>
