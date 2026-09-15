<script setup lang="ts">
  import Button from "./Button.vue";
  import CheckMark from "./CheckMark.vue";

  defineProps(['todo'])
  defineEmits(["delete","check"])
</script>

<template>
  <li class="container" :class="{done: todo.done}">
    <CheckMark :checked="todo.done" @on-check="$emit('check')" />
    <p>{{todo.text}}</p>
    <Button text="x" @click="$emit('delete')" type="delete" aria-label="delete"/>
  </li>
</template>

<style scoped>
  li {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    justify-items: center;
    align-content: center;
    align-items: center;
    margin: 1rem;
    width: 90%;
    border: 1px solid var(--main-color);
    padding: var(--main-padding);
    border-radius: var(--main-border-radius);
  }

  .done {
    border: none;
    background-color: var(--inactive-color);
    color: var(--inactive-text);
  }

  .done p {
    text-decoration: line-through;
  }

</style>