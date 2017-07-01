<template>
  <li>
    <input type="checkbox" :checked="todo.done"/>
    <span>{{todo.task}}</span>
  </li>
</template>

<script lang="ts">
  import Todo from '@/models/todo'
  import {Vue, Prop, Component} from 'vue-property-decorator'

  @Component({
    name: 'todo-list-item'
  })
  export default class TodoListItem extends Vue {

    @Prop({default: false})
    todo: Todo
  }

</script>

<style>

</style>
