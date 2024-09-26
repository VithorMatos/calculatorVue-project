<script setup>
import { reactive } from 'vue';

const estado = reactive({
  num1: 0,
  num2: 0,
  operacao: '+',
});

const calcularResultado = () => {
  const { num1, num2, operacao } = estado;

  switch (operacao) {
    case '+':
      return num1 + num2;
    case '-':
      return num1 - num2;
    case '*':
      return num1 * num2;
    case '/':
      if (num2 !== 0) {
        return num1 / num2;
      } else {
        return 'Erro: Divisão por zero'; 
      }
    default:
      return 0;
  }
};

const atualizaNum1 = (evento) => {
  estado.num1 = Number(evento.target.value);
};

const atualizaNum2 = (evento) => {
  estado.num2 = Number(evento.target.value);
};

const atualizaOperacao = (evento) => {
  estado.operacao = evento.target.value;
};
</script>

<template>
  <div class="container">
    <h1>Calculadora Aritmética</h1>
    <div>
      <input type="number" :value="estado.num1" @input="atualizaNum1"/>
      <select :value="estado.operacao" @change="atualizaOperacao">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">×</option>
        <option value="/">÷</option>
      </select>
      <input type="number" :value="estado.num2" @input="atualizaNum2"/>
    </div>
    <div>
      <h2>Resultado: {{ calcularResultado() }}</h2> 
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  margin: 0 auto;

  padding: 20px;
  border-radius: 10px;
  box-shadow: 0px 0px 2px 2px rgba(0, 0, 0, 0.295);
  max-width: 400px;
  width: 100%;
  text-align: center;
}

h1 {
  margin-bottom: 20px;
  font-size: 24px;
  color: #333;
}

input, select {
  width: 320px;
  text-align: center;
  padding: 10px;
  margin: 10px 0;
  border: 1px solid #ddd;
  border-radius: 5px;
  font-size: 16px;
}

select {
  width: 80px;
  font-size: 20px;
  font-weight: bold;
}

h2 {
  margin-top: 20px;
  font-size: 22px;
  color: #444;
}
</style>
