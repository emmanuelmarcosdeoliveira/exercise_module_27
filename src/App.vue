<script setup>
import {reactive} from 'vue';
const description = "Exercício Vue.js Calculadora Aritmética"
const image = "https://png.pngtree.com/png-vector/20190803/ourlarge/pngtree-calculator-calculation-math-progress-graph-flat-color-icon-v-png-image_1648951.jpg"
const imageCheck  = "https://media.istockphoto.com/id/1204658131/pt/vetorial/green-tick-and-confirm-icon-vector-design.jpg?s=612x612&w=0&k=20&c=kdV77-mv6KmDStWhg3atx2NxH-kt1i0vTFhvSJSWvww=";

const iamgeError = "https://media.istockphoto.com/id/1152189152/pt/vetorial/red-alert-icon.jpg?s=612x612&w=0&k=20&c=lG4TvBvOnp6cAWl3A0cJk2Krt_7rtvFBcyfiVl_MJTk="

const exibeImagem  = true;
const certo = true;
const errado = false;

const estado = reactive({
  contador: 0,
  email: " ",
  saldo: 5000,
  transferindo: 0,
  primeiroNumero: " ",
  segundoNumero: " ",
}) 

function incrementar() {
  estado.contador ++
}
function decrementar() {
  estado.contador --
}





function incluiEmail(evento){
estado.email = evento.target.value;
}
function saldoFuturo(){
  const {saldo, transferindo} = estado
  return saldo - transferindo
}
function validaValorTransf() {
  const {saldo, transferindo} = estado
  return saldo >= transferindo
}



function incluiPrimeiroNumero(evento){
  estado.primeiroNumero = evento.target.value;
} 

function incluiSegundoNumero(evento){
  estado.segundoNumero = evento.target.value;
} 


function somar() {
  const {primeiroNumero, segundoNumero}  = estado
  return primeiroNumero + segundoNumero;
}
function subtrair() {
  const {primeiroNumero, segundoNumero}  = estado
  return primeiroNumero - segundoNumero;
}
function dividir() {
  const {primeiroNumero, segundoNumero}  = estado
  return primeiroNumero / segundoNumero;
}
function multiplicar() {
  const {primeiroNumero, segundoNumero}  = estado
  return primeiroNumero * segundoNumero;
}





</script>

<template>
  <form>
    <img v-show="exibeImagem" :src="image" alt="Calculadora Aritmética">
    <h1>{{ description }}</h1>
    <!-- Inputs -->
    <p>{{ estado.primeiroNumero }}</p>
    <input @keyup="incluiPrimeiroNumero" type="number" name="" id="" placeholder="Insira um Numero"> 
    <p>{{ estado.segundoNumero }}</p>
    <input @keyup="incluiSegundoNumero" type="number" name="" id="" placeholder="Inira outro Numero">
    <input type="number" name="" id="" placeholder="Resultado">
    
    <img v-if="certo" :src="imageCheck" alt="Corect">
    <img v-else-if="errado" :src="iamgeError" alt="Error">
    <h2  v-else>Está faltando algo☹️</h2>
  </form>
  <br>
  <hr>
  <h1>{{ estado.contador }}</h1>
  <button @click="incrementar" type:button>+</button>
  <button @click="decrementar" type:button>-</button>
  <br>
  <hr>
<h1>{{ estado.email }}</h1>
<input type="email" @keyup="incluiEmail" name="" id="" placeholder="e-mail">
<br>
<br>
<hr>
Saldo: {{ estado.saldo }} 
<br>
Trasnferindo: {{ estado.transferindo }} 
<br>
<input class="campo" :class="{invalido: !validaValorTransf()}" @keyup="evento => estado.transferindo = evento.target.value  " type="number" name="" id="" placeholder="Quantia para transferir"> <br>
Saldo Após transferencia:  {{ saldoFuturo() }}

<h2>Insira um numero: {{ estado.primeiroNumero }}</h2>


</template>

<style scoped>
img {
  max-width: 150px;
  display: block;
}

.invalido {
  outline-color: red;
  border-color: red;
}
.campo {
  background: yellowgreen;
}

input {
  display: block;
}


</style>
