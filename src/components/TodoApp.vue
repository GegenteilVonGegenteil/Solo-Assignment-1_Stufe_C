<script setup lang="ts">
    import { useLocalStorage } from '@vueuse/core';
    import type {Todo} from "../modal/todo.ts";
    import CreateTodo from "./CreateTodo.vue";
    import TodoList from "./TodoList.vue";

    const todos = useLocalStorage<Todo[]>('todos',[]);

    function addTodo(newText : string) {
      const newTodo: Todo =
          {
            text: newText,
            done: false,
            id: Date.now()
          }
      todos.value.push(newTodo)
    }

    function deleteTodo(id: number) {
      const index = todos.value.findIndex(todo => todo.id === id)
      if (index !== -1) {
        todos.value.splice(index, 1)
      }
    }

    function checkTodo(id: number) {
      const index = todos.value.findIndex(todo => todo.id === id)
      if (index !== -1) {
        todos.value[index].done = !todos.value[index].done
      }
    }
</script>

<template>
      <CreateTodo @add="addTodo"/>
      <TodoList :todos="todos" @delete="deleteTodo" @check="checkTodo"/>
</template>

<style>

</style>