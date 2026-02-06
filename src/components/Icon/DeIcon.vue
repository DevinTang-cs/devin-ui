<template>
  <i class="de-icon">
    <font-awesome-icon icon! v-bind="$props" />
  </i>
</template>

<script setup lang="ts">
import type { FontAwesomeIconProps } from "@fortawesome/vue-fontawesome";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";

defineOptions({
  name: 'DeIcon',
  inheritAttrs: false,
})
defineProps<FontAwesomeIconProps>()

</script>

<style scoped>

</style>
