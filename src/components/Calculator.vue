<template>
    <div class="calculator flex flex-col items-center mt-8">
      <input type="number" v-model.number="num1" placeholder="Enter first number" class="input-field" />
      <input type="number" v-model.number="num2" placeholder="Enter second number" class="input-field" />
      <select v-model="operator" class="operator-select">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
      <button @click="calculate" class="calculate-btn">Calculate</button>
      <div v-if="result !== null" class="result mt-4">Result: {{ result }}</div>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    setup() {
      const num1 = ref(0);
      const num2 = ref(0);
      const operator = ref('+');
      const result = ref(null);
  
      const calculate = () => {
        switch (operator.value) {
          case '+':
            result.value = num1.value + num2.value;
            break;
          case '-':
            result.value = num1.value - num2.value;
            break;
          case '*':
            result.value = num1.value * num2.value;
            break;
          case '/':
            result.value = num1.value / num2.value;
            break;
          default:
            result.value = null;
        }
      };
  
      return { num1, num2, operator, result, calculate };
    }
  };
  </script>
  
  <style scoped>
  .input-field, .operator-select {
    @apply block w-full py-2 px-3 rounded border border-gray-400 mb-4;
  }
  
  .calculate-btn {
    @apply bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded;
  }
  
  .result {
    @apply text-lg font-bold mt-4;
  }
  </style>