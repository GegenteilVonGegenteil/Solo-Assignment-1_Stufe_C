<script setup lang="ts">
import TodoApp from "./components/TodoApp.vue";

</script>

<template>
  <div id="mainContainer">
    <h1>Todo App</h1>
    <TodoApp />
  </div>
</template>

<style>
  :root {
    --main-color: #412047;
    --main-text: #1f0425;
    --main-padding: 0.5rem 1rem;
    --main-border-radius: 0.5rem;
    --inactive-color: #bbb9bd;
    --inactive-text: #49454c;

    color: var(--main-text);
  }

  h1 {
    font-size: 2em;
  }

  #mainContainer {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 90vw;
  }
</style>
