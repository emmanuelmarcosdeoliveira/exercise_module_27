<script setup>
const props = defineProps(['num1', 'num2', 'tipoDeOperacao', 'resultado'  ])
</script>

<template>


 <form class="border  rounded-2 p-4 bg-info-subtle">
      <div class="row  d-flex justify-content-center">
        <div class="col-md-2">
         
          <label for="" class="">Insira um Número</label>
          <input @keyup="props.num1"
          class="form-control" type="number" name="" id="" placeholder="Insira um Numero">
        </div>

        <div class="col-md-1">
          <select @change="props.tipoDeOperacao" class="form-control mt-4">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="*">*</option>
            <option value="/">/</option>
          </select>
        </div>
       
        <!-- Input primeiro Numero -->
        <div class="col-md-2">
         <label class="for-control" for="">Insira um Número</label>
          <input @keyup="props.num2" class="form-control" type="number" name="" id="" placeholder="Inira outro Numero">
        </div>

        <!-- Input "=" -->
        <div class="col-md-1">
         
          <input class="form-control mt-4" type="text" name="" id="" placeholder="=">
        </div>

        <!-- Input Segundo Numero -->
        <div class="col-md-2 meuResultado ">
       
          <span  v-if="props.num1 && props.num2 !== '' ">{{props.resultado}} </span>
          <span v-else-if="props.num1 || pros.num2 === ''">Digite os valores para ver o Resultado</span>
        </div>
      </div>
    </form>
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