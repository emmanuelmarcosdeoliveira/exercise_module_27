<script setup>
import { reactive } from 'vue';
import Cabecalho from "./components/Cabecalho.vue"
import Formulario from './components/Formulario.vue'

const estado = reactive({
  primeiroNumero: 0,
  segundoNumero:  0,
  tipoDeOperacao: '+',
})

const resultado = () => {
  const { tipoDeOperacao } = estado
  switch (tipoDeOperacao) {
    case '-':
      return parseFloat(estado.primeiroNumero) - parseFloat(estado.segundoNumero);
    case '/':
      return parseFloat(estado.primeiroNumero) / parseFloat(estado.segundoNumero)
    case '*':
      return  parseFloat(estado.primeiroNumero) * parseFloat(estado.segundoNumero);
    default:
      return parseFloat(estado.primeiroNumero) + parseFloat(estado.segundoNumero);
  }
}  
</script>

<template>
  <div class="container">
    <!-- Cabecalho -->
    <Cabecalho />
        <!-- Formulário -->
    <Formulario :num1="evento => estado.primeiroNumero = evento.target.value"  :num2="evento => estado.segundoNumero = evento.target.value"  :tipo-deoperacao="evento => estado.tipoDeOperacao = evento.target.value"  :resultado="resultado()" />
     
  </div>
</template>

<style scoped>


</style>
