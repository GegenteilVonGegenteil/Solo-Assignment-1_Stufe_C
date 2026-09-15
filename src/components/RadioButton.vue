<script setup lang="ts">
  defineProps([
      'id',
      'name',
      'value',
      'label'
  ])

  const model = defineModel();
</script>

<template>
  <span class="radioInput">
    <input
      :id="id"
      type="radio"
      :name="name"
      :value="value"
      :checked="value"
      v-model="model"
      class="radioInputControl"
    />
    <label :for="id" class="radioInputLabel">
      <slot>{{label}}</slot>
    </label>
  </span>
</template>

<style scoped>
  .radioInput{
    display: flex;
    align-items: center;
    padding-left: 0.2rem;
    margin-bottom: 0.2rem;
    cursor: pointer;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }

  .radioInputControl{
    position: absolute;
    opacity: 0;
    cursor: pointer;
    height: 0;
    width: 0;
  }

  .radioInputLabel {
    position: relative;
    padding-left: 1.4rem;
    cursor: pointer;
    user-select: none;
  }

  .radioInputLabel::before {
    content: "";
    position: absolute;
    left: 0;
    top: 50%;
    transform: translateY(-50%);
    width: 0.5rem;
    height: 0.5rem;
    border-radius: 50%;
    border: 0.2rem solid var(--inactive-color);
    background: white;
  }


  .radio-input__control:checked + .radio-input__label::after {
    content: '';
    position: absolute;
    left: 0.28rem;
    top: 50%;
    transform: translateY(-50%);
    width: 0.55rem;
    height: 0.55rem;
    border-radius: 50%;
  }

  .radioInputControl:checked + .radioInputLabel::before {
    border-color: var(--main-color);
  }

  .radioInputControl:focus-visible + .radioInputLabel::before {
    outline: 2px solid var(--main-color);
    outline-offset: 2px;
  }
</style>