<template>
  <div>
    <div v-for="todo in todos" :key="todo.Id">
      <todo :todo="todo" />
    </div>
  </div>
</template>

<script>
import Todo from './Todo';

export default {
  props: {
    todos: Array
  },
  components: {
      'todo': Todo
  }
};
</script>