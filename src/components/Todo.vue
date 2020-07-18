<template>
  <div>
    <h1>{{ todo.Title }}</h1>
    <p>{{ todo.Content }}</p>
    <p>{{todo.Username}}</p>
    <p>{{todo.Created}}</p>
    <p>{{todo.Updated}}</p>
    <input type="checkbox" name="done" id="done" :checked="todo.Done" @click="changeTodoState">
  </div>
</template>

<script>
import axios from 'axios';

export default {
  props: {
    todo: Object
  },
  methods: {
    changeTodoState: function() {
      axios.put(`http://localhost:3000/todos/${this.todo.Id}/done`).then(response => {
      console.log(response);
    });
    }
  },
};
</script>

