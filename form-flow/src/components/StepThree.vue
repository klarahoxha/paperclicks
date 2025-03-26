<template>
    <div class="step-container">
      <h1 class="title">Summary of Your Details</h1>
  
      <div class="summary-box">
        <p><strong>Preferred Time:</strong> {{ formData.time }}</p>
        <p><strong>First Name:</strong> {{ formData.firstName }}</p>
        <p><strong>Last Name:</strong> {{ formData.lastName }}</p>
        <p><strong>Email:</strong> {{ formData.email }}</p>
        <p><strong>Phone:</strong> {{ formData.phone }}</p>
      </div>
  
      <button class="confirm-btn" @click="confirm">CONFIRM</button>
    </div>
  </template>
  
  <script setup>
  defineProps({
    formData: Object
  })
  
  const emit = defineEmits(['confirm'])
  
  const confirm = () => {
    emit('confirm')
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
  
  .summary-box {
    background-color: #f7f7f7;
    border-radius: 0.5rem;
    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.08);
    margin: 0 auto 2rem;
    max-width: 25rem;
    padding: 1.25rem;
    text-align: left;
  }
  
  .summary-box p {
    margin: 0.75rem 0;
  }
  
  .confirm-btn {
    background-color: #5c85ff;
    border: none;
    border-radius: 0.375rem;
    color: white;
    cursor: pointer;
    font-size: 1rem;
    font-weight: bold;
    padding:  0.75rem 2rem;
  }
  </style>
  