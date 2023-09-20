<script setup>
  import { reactive } from 'vue';
  import Cabecalho from './components/Cabecalho.vue';
  import Fomulario from './components/Formulario.vue';
  import Resultado from './components/Resultado.vue';

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
    <Cabecalho cabecalho></Cabecalho>
    <Fomulario :input-valor-a="evento => estado.valorA = evento.target.value" :input-valor-b="evento => estado.valorB = evento.target.value" :trocar-filtro="evento => estado.filtro = evento.target.value"></Fomulario>
    <Resultado :nome-funcao="nomeFuncaoAritmetica()" :resultado="funcaoAritmetica()"></Resultado>
  </div>
</template>

<style scoped>

</style>
