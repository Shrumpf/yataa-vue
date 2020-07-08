<template>
    <div>
        <todoList :todos="todos" />
        <button type="button" @click="clickButton">Test</button>
    </div>
</template>

<script>
import axios from "axios";
import io from "socket.io-client";
import TodoList from '../components/TodoList';

let socket = null;

export default {
    data() {
    return {
      todos: []
    };
  },
  created() {
    socket = io("http://localhost:3000");
    socket.on("connect", function() {
      console.log("connected");
    });    
  },
  mounted() {
    axios.get("http://localhost:3000/todos").then(response => {
      this.todos = response.data;
    });
    socket.on("pushedTodo", data => {
      console.log(data.data);
      this.todos.push(data.data);
    });
  },
  methods: {
    clickButton: function() {
      socket.emit("clicked");
    }
  },
    components: {
        'todoList': TodoList
    }
}
</script>