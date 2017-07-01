<template>
  <div>
    <input @keydown.enter="addTodo(newtask)" type="text" v-model="newtask"/>
    <button @click="addTodo(newtask)">Add</button>
    <button @click="todos.reverse()">Flip</button>
    <button @click="todos = []">Clear</button>
    <ul id="todo-list">
      <todo-list-item v-for="todo in todos" :todo="todo" :key="todo.id"></todo-list-item>
    </ul>
  </div>
</template>

<script lang="ts">
  import {Vue, Component} from 'vue-property-decorator'
  import Todo from '@/models/todo'
  import TodoListItem from '@/components/TodoListItem'

  @Component({
    components: {
      TodoListItem
    }
  })
  export default class TodoList extends Vue {
    newtask: String = ''

    todos= [
      {id: 1, task: 'First task', done: true},
      {id: 2, task: 'Second task', done: false}
    ]
    addTodo (newtodo) {
      this.todos.push(new Todo(this.todos.length + 1, newtodo, false))
    }
  }
</script>

<style>
#todo-list {
  width: 300px;
  margin-left: auto;
  margin-right: auto;
  text-align: left;
}
</style>
