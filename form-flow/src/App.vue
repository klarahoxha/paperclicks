<template>
  <div class="layout">
    <TheHeader />
    <MultiStepForm/>
    <TheFooter v-if="showFooter"/>
  </div>
</template>

  <script setup>
  import TheHeader from './components/TheHeader.vue'
  import MultiStepForm from './components/MultiStepForm.vue'
  import TheFooter from './components/TheFooter.vue'

  import {ref} from 'vue';

  const showFooter = ref(true);
  </script>

<style scoped>
.layout {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.layout > * {
  flex-shrink: 0;
}
</style>