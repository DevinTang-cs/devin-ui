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
  <section>
    <div class="row">
      <DeButton>Default</DeButton>
      <DeButton type="primary">Primary</DeButton>
      <DeButton type="success">Success</DeButton>
      <DeButton type="warning">Warning</DeButton>
      <DeButton type="danger">Danger</DeButton>
      <DeButton type="info">Info</DeButton>
    </div>
  </section>

  <section>
    <div class="row">
      <DeButton plain>Default</DeButton>
      <DeButton type="primary" plain>Primary</DeButton>
      <DeButton type="success" plain>Success</DeButton>
      <DeButton type="warning" plain>Warning</DeButton>
      <DeButton type="danger" plain>Danger</DeButton>
      <DeButton type="info" plain>Info</DeButton>
    </div>
  </section>

  <section>
    <div class="row">
      <DeButton round>Round Button</DeButton>
      <DeButton type="primary" round>Primary Round</DeButton>
      <DeButton type="success" circle>√</DeButton>
      <DeButton type="danger" circle>X</DeButton>
      <DeButton type="info" circle>i</DeButton>
    </div>
  </section>

  <section>
    <div class="row">
      <DeButton size="large">Large</DeButton>
      <DeButton>Default</DeButton>
      <DeButton size="small">Small</DeButton>
    </div>
  </section>

  <section>
    <div class="row">
      <DeButton disabled>Disabled Default</DeButton>
      <DeButton type="primary" disabled>Disabled Primary</DeButton>
      <DeButton type="success" plain disabled>Disabled Plain Success</DeButton>
    </div>
  </section>

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
    <!-- {{ openedValue }} -->
  </DeCollapse>
</template>

<style scoped>

</style>
