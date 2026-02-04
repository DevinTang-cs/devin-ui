<template>
  <div class="de-collapse">
    <slot></slot>
  </div>
</template>

<script setup lang="ts">
import { provide, ref, watch } from 'vue';
import { collapseContextKey, type NameType, type CollapseEmits, type CollapseProps } from './types';
defineOptions({
  name: 'DeCollapse'
})

const props = defineProps<CollapseProps>()
const emits = defineEmits<CollapseEmits>()

const activeNames = ref<NameType[]>(props.modelValue)

watch(() => props.modelValue, () => {
  activeNames.value = props.modelValue
})

if(props.accordion && activeNames.value.length > 1) {
  console.warn('[DeCollapse]: accordion mode only allow one active item at the same time')
}

const handleItemClick = (item: NameType) => {
  if (props.accordion) {
    activeNames.value = [ activeNames.value[0] === item ? '' : item ]
  } else {
    const index = activeNames.value.indexOf(item)
    if (index > -1) {
      activeNames.value.splice(index, 1)
    } else {
      activeNames.value.push(item)
    }
  }
  emits('update:modelValue', activeNames.value)
  emits('change', activeNames.value)
}

provide(collapseContextKey, {
  activeNames,
  handleItemClick
})
</script>

<style scoped>

</style>
