<template>
  <!-- Template must have a root element -->
  <div class="container">
    <h2>Gerencie seus afazeres! Seu vagal</h2>
    <div class="row m-auto">
      <div class="form-group mx-sm-3 mb-2">
        <input
          class="col-5"
          placeholder="To-do"
          v-model="currentTodo"
          type="text"
          @keyup.enter="add(currentTodo)"
          id="todoInsert"
        />
        <button class="btn btn-primary mb-2" @click="add(currentTodo)">
          Add
        </button>
      </div>
    </div>
    <ul class="list-group">
      <li
        class="list-group-item list-group-item-primary"
        :class="todo.done && 'list-group-item-success'"
        v-for="todo in todos"
        :key="todo.id"
        @click="complete(todo)"
      >
        <div class="row">
          <div class="col-md-11">
            {{ todo.name }}
          </div>
          <div class="col-md-1 d-flex justify-content-end">
            <button class="btn-close" @click="remove(todo)"></button>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: " TodoList",
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
      if (this.currentTodo.length) {
        this.todos.push({
          id: this.genId(), //.. gera um novo id
          name: todo,
          done: false,
        });
      }      
      this.currentTodo = ""; //..limpa os dados
      this.focusTodoInsert();
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
      this.focusTodoInsert()
    },
    complete(todo) {
      todo.done = !todo.done;
      this.focusTodoInsert();
    },
    focusTodoInsert(){
      document.getElementById('todoInsert').focus();      
    }
  },
};
</script>

<style scoped>
h2 {
  text-align: center;
}

li {
  cursor: pointer;
  user-select: none;
  list-style-position: ;
}

.complete {
  text-decoration: line-through;
  color: green;
}

.container {
  max-width: 50%;
  margin: auto;
  border: solid 1px darkblue;
  border-radius: 5px;
  padding-bottom: 10px;
}

#todoInsert {
  margin: 5px;
}
</style>