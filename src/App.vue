<script setup>
  import { reactive } from 'vue';  
  
  const estado = reactive({
    operacao: 'operacao',
    number1: null,
    number2: null,
    resultado: null,
  });

  const selectOperacao = (n1, n2) => {
    const {operacao} = estado;

    switch(operacao) {
      case "multiplicacao":
        return mult(n1, n2);
      case "divisao":
        return divi(n1, n2);
      case "soma":
        return som(n1,n2);
      case "subtracao": 
        return sub(n1, n2);
    }
  }

  const mult = (n1, n2) => n1 * n2;
  const divi = (n1, n2) => n1 / n2;
  const som = (n1, n2) => n1 + n2;
  const sub = (n1, n2) => n1 - n2;
</script>

<template>
  <main>
    <div class="container">
    <h1 class="title pt-3 ps-3">Calculadora</h1>
    <div class="row p-5 row_input">
      <div class="">
        <input @keyup="event => estado.number1 = event.target.valueAsNumber" class="form-control mb-2" type="number" placeholder="Digite um número">
        <input @keyup="event => estado.number2 = event.target.valueAsNumber" class="form-control mb-2" type="number" placeholder="Digite um número">
      </div>
      <div class="">
        <select @change="event => estado.operacao = event.target.value" class="form-control" name="operacoes" id="opcs">
          <option value="operacao">Operação ↓</option>
          <option value="multiplicacao">Multiplicação</option>
          <option value="divisao">Divisão</option>
          <option value="soma">Soma</option>
          <option value="subtracao">Subtração</option>
        </select> <br/>
        <h5 id="resultado" class="p-3 m-0">Resultado: <i>{{ selectOperacao(estado.number1, estado.number2) }}</i></h5>
      </div>
    </div>
  </div>
  </main>
</template>

<style scoped>
  main {
    background-color: #040c0e;
    height: 100vh;
    display: flex;
    color: #be9063;
  }
  .container {
    max-width: 400px;
    width: 100%;
    margin: 10% auto;
    background-color: #132226;
    max-height: 400px;
  }

  .form-control,.form-control:focus {
    background-color: #A4978e;
    color: #040c0e;
  }

  

  #opcs {
    text-align: center;
  }

  #resultado {
    margin-bottom: 30px
  }
</style>
