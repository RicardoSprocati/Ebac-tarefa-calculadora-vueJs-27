<script setup>
import { reactive } from 'vue';
import {ref} from 'vue';
import { computed } from 'vue';

const estado = reactive({
  filtro: '+'
})

const valorA = ref(0);
const valorB = ref(0);



const soma = (a, b) => {
  return a + b;
}
const subtracao = (a, b) => {
  return a - b;
}
const divisao = (a,  b) => {
  return a / b;
}
const multi = (a, b) => {
  return a * b;
}

const resultado = computed(() =>{

  switch (estado.filtro) {
    case '-':
      return subtracao(valorA.value,valorB.value);
    case '*':
      return multi(valorA.value,valorB.value);
    case '/':
      return divisao(valorA.value,valorB.value);  
    default: '+'
      return soma(valorA.value,valorB.value);
  }
});
</script>

<template>
  <form class="row mt-5">
    <div class="col-md-1">
      <input type="number" placeholder="Digite o valor A" class="form-control" v-model.number="valorA">
    </div>
    <div class="col-md-1">
      <select class="form-control" v-model="estado.filtro">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
    </div>
    <div class="col-md-1">
      <input type="number" placeholder="Digite o valor B" class="form-control" v-model.number="valorB">
    </div>
    <div class="col-md-2">
      <h3>Resultado: <span>{{ resultado }}</span></h3>
    </div>
  </form>
</template>

<style scoped></style>
