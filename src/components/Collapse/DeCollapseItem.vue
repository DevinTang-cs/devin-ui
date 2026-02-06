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
      <DeIcon icon="angle-right" class="header-angle" />
    </div>
    <Transition name="slide" v-on="transitionEvents" >
      <div class="de-collapse-item__wrapper"  v-show="isActive">
        <div class="de-collapse-item__content" :id="`item-content--${name}`">
          <slot></slot>
        </div>
      </div>
    </Transition>
  </div>
</template>

<script setup lang="ts">
import { collapseContextKey, type CollapseItemProps } from './types';
import DeIcon from '../Icon/DeIcon.vue';
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

const transitionEvents: Record<string, (el: HTMLElement) => void> = {
  beforeEnter(el) {
    el.style.height = '0px'
    el.style.overflow = 'hidden'
  },
  enter(el) {
    el.style.height = el.scrollHeight + 'px'
  },
  afterEnter(el) {
    el.style.height = ''
    el.style.overflow = ''
  },
  beforeLeave(el) {
    el.style.height = el.scrollHeight + 'px'
    el.style.overflow = 'hidden'
  },
  leave(el) {
    el.style.height = '0px'
  },
  afterLeave(el) {
    el.style.height = ''
    el.style.overflow = ''
  }
}
</script>

<style scoped>

</style>
