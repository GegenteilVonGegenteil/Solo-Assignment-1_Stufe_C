<script setup lang="ts">
  const props = defineProps(['text', 'type', 'ariaLabel'])
  defineEmits(["onTrigger"])
</script>

<template>
  <button :class="props.type" @click="$emit('onTrigger')" type="button" :aria-label="props.ariaLabel">
    {{props.text}}
  </button>
</template>

<style scoped>
  button {
    border-radius: var(--main-border-radius);
    border: none;
    color: #fff8f8;
    padding: 0.2em 0.55em;
    text-decoration: none;
  }

  .main {
    background-color: #5162ef;
  }

  .main:hover {
    background-color: #303eb1;
  }

  .delete {
    background-color: #da3b3b;
  }

  .delete:hover {
    background-color: #a1312e;
  }
</style>