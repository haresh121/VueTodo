<template>
  <div class="home">
    <TodoApp/>
  </div>
</template>

<script>
// @ is an alias to /src
import TodoApp from '@/components/TodoApp.vue'

export default {
  name: 'home',
  components: {
    TodoApp
  }
}
</script>
