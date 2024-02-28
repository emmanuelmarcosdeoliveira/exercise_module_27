<script setup>
import { reactive } from 'vue';
import Cabecalho from "./components/Cabecalho.vue"

const estado = reactive({
  primeiroNumero: "",
  segundoNumero: "",
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
{{estado.primeiroNumero.value}}
</script>

<template>
  <div class="container">
    <Cabecalho />
    <!-- Formulário -->
    <form class="border  rounded-2 p-4 bg-info-subtle">
      <div class="row  d-flex justify-content-center">
        <div class="col-md-2">
         
          <label for="" class="">Insira um Número</label>
          <input @keyup="evento => estado.primeiroNumero = evento.target.value"
          class="form-control" type="number" name="" id="" placeholder="Insira um Numero">
        </div>

        <div class="col-md-1">
          <select @change="evento => estado.tipoDeOperacao = evento.target.value" class="form-control mt-4">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="*">*</option>
            <option value="/">/</option>
          </select>
        </div>
       
        <!-- Input primeiro Numero -->
        <div class="col-md-2">
         <label class="for-control" for="">Insira um Número</label>
          <input @keyup="evento => estado.segundoNumero = evento.target.value" class="form-control" type="number" name="" id="" placeholder="Inira outro Numero">
        </div>

        <!-- Input "=" -->
        <div class="col-md-1">
         
          <input class="form-control mt-4" type="text" name="" id="" placeholder="=">
        </div>

        <!-- Input Segundo Numero -->
        <div class="col-md-2 meuResultado ">
       
       <span  v-if="estado.primeiroNumero && estado.segundoNumero !='' ">{{ resultado().toFixed(2) }} </span>
       <span v-else>Digite os valores para ver o Resultado</span>
        </div>
      </div>
    </form>


  </div>
</template>

<style scoped>
::placeholder, option {
  text-align: center;
  font-size: 12px;
}
.meuResultado {
  margin-top: 22px;
  font-size: 24px;
}
span {
  display: block;
  font-size: 0.75rem;
  text-wrap: nowrap;
  padding-top: 10px;
}
</style>
