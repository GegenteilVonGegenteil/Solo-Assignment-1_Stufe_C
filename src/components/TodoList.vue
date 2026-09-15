<script setup lang="ts">

import TodoItem from "./TodoItem.vue";
import {computed, ref} from "vue";
import type {Todo} from "../modal/todo.ts";
import RadioButton from "./RadioButton.vue";
  const props = defineProps(['todos'])
  defineEmits(["delete", "check"])

  const filter = ref("")

  const filteredTodos = computed(() =>
    props.todos.filter(
        (todo: Todo) => !filter.value.trim() || filter.value === String(todo.done)
    )
  )
</script>

<template>
  <section class="listContainer">
    <h2>Todos:</h2>
    <fieldset>
      <legend>Filter Todos:</legend>
      <RadioButton id="all" name="filter" value="" v-model="filter" label="All" />
      <RadioButton id="open" name="filter" value="false" v-model="filter" label="Open" />
      <RadioButton id="close" name="filter" value="true" v-model="filter" label="Done" />
    </fieldset>
    <ul>
      <TodoItem
          v-for="(todo) in filteredTodos"
          :key="todo.id"
          :todo="todo"
          @delete="$emit('delete', todo.id)"
          @check="$emit('check', todo.id)"
      />
    </ul>
  </section>
</template>

<style scoped>
  section {
    display: flex;
    flex-direction: column;
    width: 90%;
    align-items: center;
    margin-top: 1rem;
  }

  h2 {
    margin: 0;
    align-self: flex-start;
  }

  ul {
    display: flex;
    flex-direction:column;
    align-items: center;
    width: 100%;
    padding: 0;
    margin: 0;
  }

  fieldset {
    border: none;
    margin-top: 0.35rem;
    display: flex;
    gap:2rem;
  }
</style>