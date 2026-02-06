<template>
  <i
    class="de-icon"
    :class="{
      [`de-icon--${type}`]: type
    }"
    :style="customStyles"
  >
    <font-awesome-icon icon! v-bind="filterdProps" />
  </i>
</template>

<script setup lang="ts">
import { omit } from "lodash-es";
import type { FontAwesomeIconProps } from "./type";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { computed } from "vue";

defineOptions({
  name: 'DeIcon',
  inheritAttrs: false,
})
const props = defineProps<FontAwesomeIconProps>()
const filterdProps = computed(() =>  omit(props, ['type', 'color']))
const customStyles = computed(() => {
  return props.color ? { color: props.color } : {}
})

</script>

<style scoped>

</style>
