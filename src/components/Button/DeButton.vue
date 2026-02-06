<template>
  <button
    ref="_ref"
    class="de-button"
    :class="{
      [`de-button--${type}`]: type,
      [`de-button--${size}`]: size,
      'is-plain': plain,
      'is-round': round,
      'is-circle': circle,
      'is-disabled': disabled,
      'is-loading': loading
    }"
    :disabled="disabled || loading"
    :autofocus="autofocus"
    :type="nativeType"

  >
    <de-icon icon="spinner" spin v-if="loading" />
    <de-icon v-if="icon" :icon="icon" />
    <span><slot /></span>
  </button>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import type { ButtonProps } from './types';
import DeIcon from '../Icon/DeIcon.vue';
withDefaults(defineProps<ButtonProps>(), {
  nativeType: 'button'
})

const _ref = ref<HTMLButtonElement>()

defineExpose({
  ref: _ref
})
</script>

<style scoped>

</style>
