<template>
  <div id="app" class="calculator">
    <h1>Calculadora Aritmética</h1>
    <div class="inputs">
      <input
        type="number"
        v-model.number="num1"
        placeholder="Digite o primeiro número"
      />
      <!-- Não esquecer!!! vou utilizar o switch-->
      <select v-model="operation"> 
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
      <input
        type="number"
        v-model.number="num2"
        placeholder="Digite o segundo número"
      />
    </div>
    <div class="result">
      <h2>Resultado: {{ result }}</h2>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';


const num1 = ref(0);
const num2 = ref(0);
const operation = ref('+');


const result = computed(() => {
  switch (operation.value) {
    case '+':
      return num1.value + num2.value;
    case '-':
      return num1.value - num2.value;
    case '*':
      return num1.value * num2.value;
    case '/':
      return num2.value !== 0 ? num1.value / num2.value : 'Erro: Divisão por 0';
    default:
      return 'Operação inválida';
  }
});
</script>

<style scoped>

.calculator {
  width: 300px;
  margin: 50px auto;
  text-align: center;
  font-family: Arial, sans-serif;
}

.inputs {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-bottom: 20px;
}

input,
select {
  padding: 10px;
  font-size: 16px;
}

.result h2 {
  color: #333;
  font-size: 20px;
  margin: 0;
}

</style>
