<script setup>
  const name = "Vue dinámico";
  const styleColor = "color: blue";
  const arrayColores = ["blue", "red", "green", "paraguay"];
  const activo = true ;
  //const arrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"];
  const counter = ref(0);
  const arrayFavoritos = ref([]);
  const arrayFrutas = [
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
  
  const increment = () => {
    counter.value++;
  }

  const decrement = () => {
    counter.value--;
  }
    
  const reset = () => {
    counter.value = 0;
  }

  const add = () => {
    arrayFavoritos.value.push(counter.value);
  }

  const blockButtonAdd = computed(() => {
    const numSearch = arrayFavoritos.value.find((number) => number === counter.value);
    return (numSearch || numSearch === 0) ? true : false;
  });

</script>

<template>
  <h1>Hola vue js</h1>
  <br>
  {{name.toUpperCase()}}
  <br>
  <h2 :style="styleColor">Soy azul</h2>

  <h2 :style="`color: arrayColores[1]`">Soy verde</h2>

  <h3>
    {{activo ? 'Estoy activo': 'Estoy inactivo'}}
  </h3>

  <h3 v-show="activo">Estoy activo con v-show</h3>

  <p v-if="activo === true">Estoy activo</p>
  <p v-else-if="activo === false">Estoy inactivo</p>
  <p v-else>Estoy indeciso</p>

  <h3 {{arrayColores}}></h3>

  <ul>
    <li v-for="(fruta, index) in arrayFrutas"
    :key="index">
      {{index}} - {{fruta}}
    </li>

    <!--li v-for="(fruta, name) in arrayFrutas"
    :key="name">
      {{name}} - {{fruta}}
    </li-->
  </ul>

  <h2>Counter:</h2>
  <h2 :class="counter >= 0 ? 'positive' : 'negative' "></h2>
  <button @click="increment">Incrementar</button>
  <button @click="decrement">Disminuir</button>
  <button @click="reset">Reset</button>
  <button @click="add" :disabled="blockButtonAdd">Add to List</button>

  {{arrayFavoritos}}
  <ul>
    <li v-for="(number, index) in arrayFavoritos"
    :key="index">
      {{number}}
    </li>

    <!--li v-for="(fruta, name) in arrayFrutas"
    :key="name">
      {{name}} - {{fruta}}
    </li-->

    <li v-for="item in arrayFrutas"
    :key="item.name">
      {{item.name}} - {{item.price}}
    </li>
  </ul>


</template>
<style>
h1{
  color: red;
}
.positive{
  color: green;
}
.negative{
  color: red;
}
.zero{
  color: peru;
}
</style>