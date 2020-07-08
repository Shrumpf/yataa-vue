<template>
  <div>
    <h1>{{ todo.Title }}</h1>
    <p>{{ todo.Content }}</p>
  </div>
</template>

<script>
export default {
  props: {
    todo: Object
  }
};
</script>

