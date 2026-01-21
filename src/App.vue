<script setup lang="ts">
  import { ref, onMounted } from 'vue';
  import DeButton from './components/Button/DeButton.vue';
  import type { ButtonInstance } from './components/Button/types';
  const buttonRef = ref<ButtonInstance | null>(null);
  onMounted(() => {
    console.log(buttonRef.value?.ref);
  })
</script>

<template>
  <DeButton type='primary' plain ref="buttonRef">Button</DeButton>
</template>

<style scoped></style>
