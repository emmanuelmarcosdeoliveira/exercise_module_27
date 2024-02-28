<script setup>
const description = "Calculadora Aritmética com Vue"
const image = "https://png.pngtree.com/png-vector/20190803/ourlarge/pngtree-calculator-calculation-math-progress-graph-flat-color-icon-v-png-image_1648951.jpg"

const exibeImagem  = true;
</script>

<template>
  
  <header class="p-5 mb-4 mt-4 rounded-4"> 
      <div class="d-flex justify-content-center align-items-center" >
        <img class="d-block" v-show="exibeImagem" :src="image" alt="Calculadora Aritmética">
        <h1>{{ description }}</h1>
      </div>
    </header>

</template>

<style scoped> 

img {
  max-width: 150px;
  display: block;
}
</style>