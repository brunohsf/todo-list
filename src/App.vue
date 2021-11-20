<template>

<div>
  <TodoList/>
</div>
</template>

<script>
import TodoList from "./components/TodoList.vue";

export default {
  name: "App",
  components: {
    TodoList,
  },
};
</script>

<style scoped>
#logo {
  margin: 5px auto;
  display: block;
}
h1 {
  text-align: center;
  color: darkblue;
}

.container {
  max-width: 50%;
  margin: auto;
}

</style>
