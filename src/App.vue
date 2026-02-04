<script setup lang="ts">
  import { ref, onMounted } from 'vue';
  import DeButton from './components/Button/DeButton.vue';
  import type { ButtonInstance } from './components/Button/types';
  import DeCollapse from './components/Collapse/DeCollapse.vue';
  import DeCollapseItem from './components/Collapse/DeCollapseItem.vue';
  const buttonRef = ref<ButtonInstance | null>(null);
  const openedValue = ref(['a'])
  onMounted(() => {
    console.log(buttonRef.value?.ref);
  })
</script>

<template>
  <DeButton type='primary' plain ref="buttonRef">Button</DeButton>
  <DeCollapse v-model="openedValue" @change="(e) => console.log(e)" accordion>
    <DeCollapseItem name="a" title="Title A">
      <h1>headline title</h1>
      <div> this is content a aaa </div>
    </DeCollapseItem>
    <DeCollapseItem name="b" title="Title B">
      <div> this is bbbbb test </div>
    </DeCollapseItem>
    <DeCollapseItem name="c" title="Disabled Title" disabled>
      <div> this is cccc test </div>
    </DeCollapseItem>
    {{ openedValue }}
  </DeCollapse>
</template>

<style scoped></style>
