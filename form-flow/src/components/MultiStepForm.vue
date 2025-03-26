<template>
    <div class="flex-grow">
    <StepOne v-if="step === 1" v-model="formData.time" @next="step = 2" />
    <StepTwo v-if="step === 2" v-model:formData="formData" @next="step = 3" />
    <StepThree v-if="step === 3" :formData="formData" @confirm="step = 4" />
    <ThankYou v-if="step === 4" />    </div>
</template>

<script setup>
import {reactive, ref} from 'vue';
import StepOne from './StepOne.vue';
import StepTwo from './StepTwo.vue';
import StepThree from './StepThree.vue';
import ThankYou from './ThankYou.vue'


const step = ref(1);

const formData = reactive({
  time: '',
  firstName: '',
  lastName: '',
  email: '',
  phone: '',
  consent: false
});
</script>

<style scoped>
.flex-grow {
  flex: 1;
  padding: 0 12rem;
}
</style>