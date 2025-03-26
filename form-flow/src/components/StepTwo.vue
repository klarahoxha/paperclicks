<template>
    <div class="step-container">
      <h1 class="title">Add Your Personal Details</h1>
  
      <form @submit.prevent="submitForm" class="form-grid">
        <input v-model="localData.firstName" type="text" placeholder="First name" required />
        <input v-model="localData.lastName" type="text" placeholder="Last name" required />
        <input v-model="localData.email" type="email" placeholder="Email" required />
        <input v-model="localData.phone" type="tel" placeholder="Phone Number" required />
  
        <div class="checkbox-wrapper">
          <input type="checkbox" id="consent" v-model="localData.consent" />
          <label for="consent">
           By clicking the button above, you acknowledge, consent and agree to the following:  
           a) Our Privacy Policy and consent to receive notices and other communications electronically;  
           b) We take your privacy seriously. You are providing express written consent for us to share your information with up to four (4) of its and for , parties calling on behalf of , or authorized third parties on their behalf to contact you (including through automated means; e.g. autodialing, text and pre-recorded messaging) about legal services or other Mass Tort related offers via telephone, mobile device (including SMS and MMS) and/or email, even if your telephone number is currently listed on any state, federal, local or corporate Do Not Call list;  
           c) Consent to be contacted is not required in order to purchase goods or services from or the that contact you. You may choose to speak with an individual service provider by dialing (888) 888-8888.
          </label>
        </div>
        
        <div class="button-wrap">
            <button
            type="submit"
            class="submit-btn"
            :disabled="!isFormValid"
            >
            SUBMIT YOUR DETAILS
        </button>
        </div>
      </form>
    </div>
  </template>
  
  <script setup>
  import { reactive, computed } from 'vue'
  
  const props = defineProps({
    formData: Object
  })
  
  const emit = defineEmits(['update:formData', 'next'])
  
  // Local copy for reactive tracking
  const localData = reactive({ ...props.formData })
  
  const isFormValid = computed(() => {
    return (
      localData.firstName &&
      localData.lastName &&
      localData.email &&
      localData.phone &&
      localData.consent
    )
  })
  
  const submitForm = () => {
    emit('update:formData', { ...localData })
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
  
  .form-grid {
    display: grid;
    gap: 1rem;
    margin: 0 auto;
    max-width: 32rem;
  }
  
  input[type='text'],
  input[type='email'],
  input[type='tel'] {
    background-color: #fafafa;
    border: 1px solid #ccc;
    border-radius: 0.375rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);
    font-size: 1rem;
    padding: 0.75rem;
    width: 100%;
  }
  
  .checkbox-wrapper {
    align-items: flex-start;
    background-color: #f8f8ff;
    display: flex;
    font-size: 12px;
    gap: 10px;
    line-height: 1.6;
    padding: 1.5rem 1rem;
    text-align: left;  
    width: 100%;
}
  
  .button-wrap{
    display: flex;
    justify-content: center;
  }

  .submit-btn {
    background-color: #5c85ff;
    border: none;
    border-radius: 0.375rem;
    color: white;
    cursor: pointer;
    font-size: 1rem;
    font-weight: bold;
    padding: 1rem 2rem;
  }
  
  .submit-btn:disabled {
    background-color: #799efe;
    cursor: not-allowed;
  }
  </style>
  