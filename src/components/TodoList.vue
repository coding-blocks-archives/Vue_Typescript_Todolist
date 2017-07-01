<template>
  <div>
    <input @keydown.enter="addTodo(newtask)" type="text" v-model="newtask"/>
    <button @click="addTodo(newtask)">Add</button>
    <button @click="todos.reverse()">Flip</button>
    <button @click="todos = []">Clear</button>
    <ul id="todo-list">
      <li v-for="todo in todos" :key="todo.id">
        <input @change="todo.done = true" type="checkbox" :checked="todo.done"/>
        <span>{{todo.task}}</span>
      </li>
    </ul>
  </div>
</template>

<script lang="js">
  import Vue from 'vue'
  import Component from 'vue-class-component'

  @Component
  export default class TodoList extends Vue {
    todos= [
      {id: 1, task: 'First task', done: true},
      {id: 2, task: 'Second task', done: false}
    ]

    addTodo (newtodo) {
      this.todos.push({
        id: this.todos.length + 1,
        task: newtodo,
        done: false
      })
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
