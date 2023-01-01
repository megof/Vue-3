<script setup>
import { ref, computed } from 'vue';

const version = "3";
const stclr = "color: blue";
const act = false;
const arrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"];
const arrayFrutasv2 = [
  {
    name: "Manzana",
    price: "$1.00",
    description: "Una manzana",
  },
  {
    name: "Pera",
    price: "$2.00",
    description: "Una pera",
  },
  {
    name: "Naranja",
    price: "$3.00",
    description: "Una naranja",
  },
];
const objfruta = {
  name: "Manzana",
  price: "$1.00",
  description: "Una manzana",
};
const onclk = (mensaje) => {
  console.log('click' + mensaje)
}

const contador = ref(0);
const col = ref('color: green');
const incremet = (numero) => {
  contador.value += numero;
  if (contador.value > 5 && contador.value < 10) {
    col.value = 'color: red';
  }

}
const encontrar = (valor) => {
  return valor === contador.value
}
const contador_computer = computed(() => {
  if (contador.value === 0) {
    return 'color: black'
  } else {
    return (contador.value > 0) ?
      'color: green' :
      'color: red'
  }
})

const Fav = ref([])//
const add = () => {
  Fav.value.push(contador.value)//
}
const add_computer = computed(() => {
  return (Fav.value.find(element => element === contador.value) === contador.value) ?
    true :
    false
})
</script>

<template>
  <div class="container text-center mt-3">
    <h1>Hola Vue {{ version }} Js</h1>
    <h2 :style="stclr">Hola Vue Js</h2>
    <h2 v-if="act">Xd1</h2><!-- si no se va a cambiar mucho-->
    <h2 v-else="act">Xd2</h2>
    <h2 v-show="act">Xd3</h2><!-- si se alterna mucho-->
    <ul class="list-group">
      <li class="list-group-item" v-for="(fruta, index) in arrayFrutas" :key="index">
        {{ fruta }}</li>
    </ul>
    <ul class="list-group">
      <li class="list-group-item" v-for="fruta in arrayFrutasv2" :key="fruta.name">
        {{ fruta.description }} - {{ fruta.price }}</li>
    </ul>
    <ul class="list-group">
      <li class="list-group-item" v-for="(value, propiedad) in objfruta" :key="value">
        {{ propiedad }} - {{ value }}</li>
    </ul>
    <button class="btn btn-primary" @click="onclk">Press me!</button>


    <button class="btn btn-success" @click="onclk('L')">Press me! L</button>
    <button class="btn btn-warning" @click.middle="onclk('M')">Press me! M</button>
    <button class="btn btn-danger" @click.right="onclk('R')">Press me! R</button>
    <button class="btn btn-secondary" @click.right.prevent="onclk('R')">Press me! R-p</button>

    <h2 :style="col">{{ contador }}</h2>
    <button class="btn btn-danger" @click="(incremet(-1))">Decremet</button>
    <button class="btn btn-success" @click="(incremet(1))">Incremet</button>
    <h2 :style="contador_computer">{{ contador }}</h2>
    <button class="btn btn-primary" @click="(add)" :disabled="add_computer">Add</button>
    
    <ul class="list-group">
      <li class="list-group-item" v-for="(value, index) in Fav" :key="index">
        {{ value }}</li>
    </ul>
  </div>

</template>
<style>
h1 {
  color: red;
}
</style>