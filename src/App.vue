<script setup>
import { reactive } from 'vue';

  const estado = reactive({
    filtro: 'soma',
    valorA: 0,
    valorB: 0,
  })

  function soma() {
    return (parseInt(estado.valorA) + parseInt(estado.valorB));
  }

  function subtracao() {
    return estado.valorA - estado.valorB;
  }

  function multiplicacao() {
    return estado.valorA * estado.valorB;
  }

  function divisao() {
    return estado.valorA / estado.valorB;
  }

  const funcaoAritmetica = () => {
    const { filtro } = estado;

    switch(filtro) {
      case 'soma':
        return soma();
      case 'subtracao':
        return subtracao();
      case 'multiplicacao':
        return multiplicacao();
      case 'divisao':
        return divisao().toFixed(2);
    }
  }

  const nomeFuncaoAritmetica = () => {
    const { filtro } = estado;

    switch(filtro) {
      case 'soma':
        return `A soma de ${estado.valorA} mais ${estado.valorB}`;
      case 'subtracao':
        return `A subtração de ${estado.valorA} menos ${estado.valorB}`;
      case 'multiplicacao':
        return `A multiplicação de ${estado.valorA} por ${estado.valorB}`;
      case 'divisao':
        return `A divisão de ${estado.valorA} por ${estado.valorB}`;
    }
  }

</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-body-secondary text-center rounded-3">
      <h1>Calculadora aritmética </h1>
    </header>
    <form class="p-5">
      <div class="row">
        <div class="col-md-4">
          <input @keyup="evento => estado.valorA = evento.target.value" type="number" placeholder="Digite o valor ''A'' " class="form-control" required>
        </div>
        <div class="col-md-4">
          <input @keyup="evento => estado.valorB = evento.target.value" type="number" placeholder="Digite o valor ''B'' " class="form-control" required>
        </div>
        <div class="col-md-4">
          <select @change="evento => estado.filtro = evento.target.value" class="form-control">
            <option value="soma">Soma</option>
            <option value="subtracao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
          </select>
        </div>
      </div>
    </form>
    <div class="text-center">
      <h2 class="mb-4">Resultado</h2>
      <p class="fs-3">{{ nomeFuncaoAritmetica() }} é igual a {{ funcaoAritmetica() }}.</p>
    </div>
</div>
</template>

<style scoped>

</style>
