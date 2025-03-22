<script setup>
import {computed, ref} from 'vue'
import Header from './components/Header.vue';
import Button from './components/Button.vue';


  const presupuesto = ref(1000000);
  const MIN = 0;
  const MAX = 2000000;
  const STEP = 50000;

  const formatearDinero = computed(()=>{
    const formatter = new Intl.NumberFormat('en-US', {
      style: 'currency',
      currency: 'USD'
    });
    return formatter.format(presupuesto.value)
  });

  const handleChangeDecremento = () => {
    const valor = presupuesto.value - STEP;
    if(valor < MIN){
      alert('Presupuesto no válido');
      return;
    }
    presupuesto.value = valor;
  }

  const handleChangeAumento = ()=>{
    const valor = presupuesto.value + STEP;
    if(valor > MAX){
      alert('Presupuesto no válido');
      return;
    }
    presupuesto.value = valor;
  }
</script>

<template>
  <div>
    <Header/>
    
    <div class="my-20 max-w-3/4 w:max-w-lg mx-auto bg-linear-to-b from-fuchsia-100 to-fuchsia-900 rounded-lg shadow p-5 text-center">
      <div class="flex justify-between">
      <Button 
         :operador="'-'"
         @fn="handleChangeDecremento"
      />
       
      <Button 
        :operador="'+'"
        @fn="handleChangeAumento"

      />
      

    </div>
      <p class="mb-2">¿Cuál es tu presupuesto?</p>
      <input 
      type="range"
      :min="MIN"
      :max="MAX"
      :step="STEP"
      :value="presupuesto"
      class="bg-fuchsia-100 accent-fuchsia-600 hover:accent-fuchsia-700   w-full rounded-lg p-1"
      v-model.number="presupuesto"
      >
      <p class="my-5 text-center font-bold text-white text-3xl"> {{ formatearDinero }}</p>
      
      <select name="" id=""
      class="w-full bg-white rounded-lg p-1 mb-3">
      <option value="">Seleccionar categoria</option>
      <option value="hogar">Hogar</option>
      <option value="comida">Comida</option>
      <option value="transportes">Transportes</option>
      <option value="educacion">Educación</option>
      <option value="ocio">Ocio</option>
      <option value="otros">Otros</option>
    </select>

    <input 
      type="num"
      class="bg-white w-full rounded-lg p-1 mb-2"
      placeholder="Ingresa el valor del gasto"
      >
    
    
  </div>
</div>
 
</template>

<style scoped>

</style>
