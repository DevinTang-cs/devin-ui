<template>
  <div
    class="de-collapse-item"
    :class="{
      'is-disabled': disabled
    }"
  >
    <div
      class="de-collapse-item__header"
      :class="{
        'is-disabled': disabled,
        'is-active': isActive
      }"
      :id="`item-header--${name}`"
      @click="handleClick"
    >
      <slot name="title">{{ title }}</slot>
    </div>
    <div class="de-collapse-item__content" :id="`item-content--${name}`" v-show="isActive">
      <slot></slot>
    </div>
  </div>
</template>

<script setup lang="ts">
import { collapseContextKey, type CollapseItemProps } from './types';
import { computed, inject } from 'vue';
defineOptions({
  name: 'DeCollapseItem'
})
const props = defineProps<CollapseItemProps>()

const collapseContext = inject(collapseContextKey)

const isActive = computed(() => collapseContext?.activeNames.value.includes(props.name))

const handleClick = () => {
  if (props.disabled) return
  collapseContext?.handleItemClick(props.name)
}
</script>

<style scoped>

</style>
