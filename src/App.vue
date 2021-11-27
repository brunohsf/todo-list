<template>
  <div>
    <Header />
    <TodoList />
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";
import Header from "./components/Header.vue";

export default {
  name: "App",
  components: {
    TodoList,
    Header,
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

</style>
