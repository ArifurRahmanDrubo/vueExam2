<template>
  <div id="app" class="container mx-auto">
    <div class="flex justify-center my-8">
     
      <button @click="showQuateDisplay" :class="{ 'bg-blue-500 text-white': activeComponent === 'quateDisplay', 'bg-gray-300': activeComponent !== 'quateDisplay' }" class="text-lg font-semibold mx-6 px-4 py-2 rounded">Quote of the Day</button>
      <button @click="showCalculator" :class="{ 'bg-blue-500 text-white': activeComponent === 'calculator', 'bg-gray-300': activeComponent !== 'calculator' }" class="text-lg font-semibold px-4 mx-6 py-2 mr-4 rounded">Calculator</button>
    </div>
    
    <div class="container mx-auto">
      <h1 v-if="activeComponent === 'quateDisplay'" class="text-3xl font-bold text-center mx-5 my-8">Quote of the Day</h1>

      <QuateDisplay v-if="activeComponent === 'quateDisplay'" />
      
      <h1 v-if="activeComponent === 'calculator'" class="text-3xl font-bold text-center mx-4 my-8">Calculator</h1>
      <Calculator v-if="activeComponent === 'calculator'" />
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
import Calculator from './components/Calculator.vue';
import QuateDisplay from './components/QuateDisplay.vue';

export default {
  name: 'App',
  components: {
    Calculator,
    QuateDisplay
  },
  setup() {
    const activeComponent = ref('');

    const showCalculator = () => {
      activeComponent.value = 'calculator';
    };

    const showQuateDisplay = () => {
      activeComponent.value = 'quateDisplay';
    };

    return {
      activeComponent,
      showCalculator,
      showQuateDisplay
    };
  }
};
</script>

<style>
/* Add global styles here if needed */
</style>

