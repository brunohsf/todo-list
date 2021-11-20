<template>
  <!-- Template must have a root element -->
  <div class="container">
    <h2>Gerencie seus afazeres! Seu vagal</h2>
    <input v-model="currentTodo" type="text" @keyup.enter="add(currentTodo)" id="todoInsert"/>
    <button @click="add(currentTodo)">Add</button>
    <ul>
      <li :class="todo.done && 'complete'" v-for="todo in todos" :key="todo.id" @dblclick="remove(todo)" @click="complete(todo)">
        {{ todo.name }}
      </li>
    </ul>
  </div>
  
</template>

<script>
export default {
  name: "TodoList",

  data: () => ({
    id: 0, //..id dos todos
    currentTodo: "", //..todo atual, vinculado ao input
    todos: [], //..array vazui para armazenar os todos
  }),

  methods: {
    //.metodos vão aqui
    genId() {
      return (this.id += 1); //..gera um id
    },
    add(todo) {
      //.. adiciona um novo todo ao array todos
      this.todos.push({
        id: this.genId(), //.. gera um novo id
        name: todo,
        done: false,
      });
      this.currentTodo = ""; //..limpa os dados
    },
    getIndex(todo) {
      let index = this.todos.findIndex(function (item) {
        return item.name === todo.name;
      });
      return index;
    },
    remove(todo) {
      let index = this.getIndex(todo);
      this.todos.splice(index, 1);
    },
    complete(todo){
        todo.done = !todo.done;
    }


  },
};
</script>

<style scoped>
h2 {
  text-align: center;
}
li{
    cursor: pointer;
    user-select: none;
    list-style-position: ;
}
.complete{
    text-decoration: line-through;
    color: green;
}

.container {
  max-width: 50%;
  margin: auto;
  border: solid 1px darkblue;
  border-radius: 5px;
}
#todoInsert {
    margin: 5px;
}
</style>