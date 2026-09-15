<script setup lang="ts">
  defineProps(['checked', 'ariaLabel'])
  defineEmits(["onCheck"])
</script>

<template>
  <label class="label">
    <input
        type="checkbox"
        :checked="checked"
        @change="$emit('onCheck')"
        :aria-label="ariaLabel"
    />
    <span class="checkbox"></span>
  </label>
</template>

<style scoped>
  .label {
    position: relative;
    cursor: pointer;
    font-size: 22px;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }

  .label input {
    opacity: 0;
    cursor: pointer;
    height: 0;
    width: 0;
  }

  .checkbox {
    position: absolute;
    top: 0;
    left: 0;
    height: 25px;
    width: 25px;
    background-color: whitesmoke;
    border-radius: 0.25rem;
    border: 1px solid var(--main-color);
    color: var(--main-color);
  }

 .checkbox:after {
    content: "";
    position: absolute;
    display: none;
  }

  .label input:checked ~ .checkbox:after {
    display: block;
  }

  .label .checkbox:after {
    left: 9px;
    top: 5px;
    width: 5px;
    height: 10px;
    border: solid var(--main-color);
    border-width: 0 3px 3px 0;
    -webkit-transform: rotate(45deg);
    -ms-transform: rotate(45deg);
    transform: rotate(45deg);
  }
</style>