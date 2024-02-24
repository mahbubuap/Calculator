<script setup>
import { ref } from 'vue';

const operand1 = ref(null);
const operand2 = ref(null);
const operator = ref('+');
const result = ref(null);

const calculate = () => {
    if (operand1.value === null || operand2.value === null) {
        result.value = null;
        return;
    }

    switch (operator.value) {
        case '+':
            result.value = operand1.value + operand2.value;
            break;
        case '-':
            result.value = operand1.value - operand2.value;
            break;
        case '*':
            result.value = operand1.value * operand2.value;
            break;
        case '/':
            result.value = operand1.value / operand2.value;
            break;
        default:
            result.value = null;
    }
};
</script>

<template>
    <div class="calculator-container p-6 bg-green-200 rounded-lg shadow-md">
        <input v-model="operand1 " type="number" placeholder="Enter first number" class="input-field  ">
        <input v-model="operand2" type="number" placeholder="Enter second number" class="input-field  ">
        <select v-model="operator" class="select-field">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="*">*</option>
            <option value="/">/</option>
        </select>
        <button @click="calculate" class="btn bg-green-500 hover:bg-green-600 text-white font-bold py-2 px-4 rounded">
            Calculate
        </button>
         <div v-if="result !== null" class="result text-lg mt-4 border-t pt-4 ">
          <span class="text-gray-700 font-semibold">Result:</span>
          <span class="text-white-500 ml-2 font-semibold">{{ result }}</span>
        </div>
    </div>
</template>



<style scoped>
.calculator-container {
    max-width: 400px;
    margin: 0 auto;
}

.input-field,
.select-field {
    margin: 10px 0;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    width: 100%;
    font-size: 16px;
}

.btn {
    margin: 10px 0;
    padding: 10px 20px;
    border: 1px solid #22c55e;
}

.result {
  margin-top: 20px;
  border-top: 1px solid #22c55e;
  padding-top: 10px;
}
.input-field{
    color:  #22c55e;
    border: 1px solid #22c55e ;
}

.select-field{
     color:  #22c55e;
    border: 1px solid #22c55e ;
}
</style>
