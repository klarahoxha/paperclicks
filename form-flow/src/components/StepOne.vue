<template>
    <div class="step-container">
      <h1 class="title">What Is The Best Time To Reach You?</h1>
  
      <select v-model="selectedTime" class="time-select">
        <option disabled value="" class="time-select-disabled">Choose Your Time</option>
        <option v-for="time in times" :key="time" :value="time" class="time-list">
          {{ time }}
        </option>
      </select>
      <p class="note">(All times are in CST)</p>
  
      <button
        :disabled="!selectedTime"
        @click="goToNextStep"
        class="continue-btn"
      >
        CONTINUE
      </button>
    </div>
  </template>
  
  <script setup>
  import { ref, watch } from 'vue'
  
  const props = defineProps({
    modelValue: String
  })
  
  const emit = defineEmits(['update:modelValue', 'next'])
  
  const selectedTime = ref(props.modelValue || '')
  
  const times = [
    '8 AM CST',
    '9 AM CST',
    '10 AM CST',
    '11 AM CST',
    '12 PM CST',
    '1 PM CST',
    '2 PM CST',
    '3 PM CST',
    '4 PM CST',
    '5 PM CST'
  ]
  
  watch(selectedTime, (value) => {
    emit('update:modelValue', value)
  })
  
  const goToNextStep = () => {
    emit('next')
  }
  </script>
  
  <style scoped>
  .step-container {
    padding: 2.5rem 1.25rem;
    text-align: center;
  }
  
  .title {
    font-size: 2rem;
    margin-bottom: 2rem;
  }
  
  .time-select {
    border: 1px solid #ccc;
    border-radius: 0.375rem;
    color: #777;
    padding: 0.75rem;
    width: 18rem;
  }

  .time-select-disabled{
    background-color: #4b4b4b;
    color: #fff;
  }

  .time-list{
    background-color: #4b4b4b;
    color: #fff;
  }

  .note {
    color: #808080;
    font-size: 0.75rem;
    margin-top: 0.5rem;
  }
  
  .continue-btn {
    background-color: #5c85ff;
    border: none;
    border-radius: 0.375rem;
    color: white;
    cursor: pointer;
    font-size: 1rem;
    font-weight: bold;
    margin-top: 1.5rem;
    padding: 1rem 2rem;
    width: 18rem;
  }
  
  .continue-btn:disabled {
    background-color: #799efe;
    cursor: not-allowed;
  }
  </style>
  