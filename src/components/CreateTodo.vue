<script setup lang="ts">
  import {ref} from "vue";
  import Button from "./Button.vue";

  const inputText = ref("")
  const emit = defineEmits(["add"])

  function addTodo() {
    if (inputText.value.trim()) {
      emit("add", inputText.value)
      inputText.value = ""
    }
  }

</script>

<template>
  <section>
    <h2>Add Todo</h2>
    <form @submit.prevent="addTodo">
      <input
          id="newTodo"
          v-model="inputText"
          placeholder="Enter Todo"
          type="text"
          aria-label="New Todo Input"
      />
      <Button text="+" @click="addTodo" type="main" aria-label="add Todo"/>
    </form>
  </section>
</template>

<style scoped>

  h2 {
    margin: 0;
  }

  form {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 1rem;
    padding: 0.2rem;
    border: 1px solid var(--main-color);
    border-radius: 5px;
    margin-top: 0.25rem;
  }

  input {
    border: none;
  }
</style>