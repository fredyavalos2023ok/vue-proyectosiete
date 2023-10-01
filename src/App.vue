<script setup>
  import { computed, ref } from 'vue'

  const name = 'Vue dinámico'
  const counter = ref(0);
  const arrayFavoritos = ref([]);

  const add = () => {
    arrayFavoritos.value.push(counter.value);
  }

  const bloquearBtnAdd = computed(() => {
    const numSearch = arrayFavoritos.value.find((num) => num === counter.value);
    console.log(numSearch);
      if(numSearch === 0) return true;
      return numSearch ? true : false;
  });

  const increment = () => counter.value ++;
  const decrement = () => counter.value --;
  const reset = () => counter.value = 0;
</script>

<template>
  <div class="container text-center" >
    <h1>{{ name.toUpperCase() }}</h1>
    <h3>{{ counter }}</h3>
    <div class="btn-group">
      <button @click="increment" class="btn btn-success">incrementar</button>
      <button @click="decrement" class="btn btn-danger">decrementar</button>
      <button @click="reset" class="btn btn-secondary">Reset</button>
      <button @click="add" :disabled="bloquearBtnAdd" class="btn btn-primary">Add</button>
    </div>
<!--<br>
    <h2>{{ arrayFavoritos }}</h2> -->
    <br>
    <br>
    <br>
    <ul class="list-group mt-4">
      <li 
        class="list-group-item"
        v-for="num in arrayFavoritos"
        :key="num.index"
        >
        {{ num }}
      </li>
    </ul>
  </div>
</template>

<style>
  h2{
    color:blue;
  }
  h1{
    color:red;
  }
  h3{
    color:peru;
  }
</style>