<template>
  <div id="app">
    <Header />
    <Todos />
    <TodoItem />

  </div>
</template>

<script>

import Header from "./components/Header.vue"
import Todos from "./components/Todos.vue"


export default {
  name: 'App',
  components: {Header , Todos}
}
</script>

<style>

</style>