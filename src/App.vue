<script setup lang="ts">
import { ref, inject } from 'vue'
import { RouterLink, RouterView} from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import AddView from './views/AddView.vue'
import HomeView from './views/HomeView.vue'

const todos = ref([])
let id = 0

const addToList = (e) => {
  todos.value.push({id: id++, text: e, done: false, date: new Date()})
}

const deleteFromList = (e) => {
  todos.value = todos.value.filter((to) => to !== e)
}

// methods: {
//   receiveEmit(todos) {

//   }
// }

</script>

<template>
  <header>
    <img
      alt="Vue logo"
      class="logo"
      src="@/assets/logo.svg"
      width="125"
      height="125"
    />

    <div class="wrapper">
      <HelloWorld msg="To Do List" />
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/add">Add</RouterLink>
      </nav>
      <!-- <HomeView :tasks="todos"/> -->
      <!-- <AddView @response="addToList"/> -->
    </div>
  </header>

  <RouterView @response="addToList" :tasks="todos" @delete="deleteFromList"/>
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
