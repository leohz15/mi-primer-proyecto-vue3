<script setup>

import { ref, computed } from 'vue';


let count = ref(0);
let numbers = ref([]);


const decrement = () => {
  console.log("decremento")
  count.value --;
  console.log(count);
}


const increment = () => {
  console.log("aumento")
  count.value ++;
  console.log(count);
};

const reset = () => {
  console.log("reseteado")
  count.value = 0;
}

const add = () => {
  numbers.value.push(count.value)
}

const del = () => {
  numbers.value.pop(numbers.value)
}

const bloquearBtnAdd = computed(() => {
  const numSearch = numbers.value.find(num => num === count.value)
  console.log(numSearch);
  return numSearch || numSearch === 0;
})

const classCounter = computed(() => {
  if (count.value === 0) {
    return 'zero'
  }
  if (count.value > 0) {
    return 'positive'
  }

  if (count.value < 0) {
    return 'negative'
  }

});

</script>
<template>
  
  <div class="main-section">
    <h1 class="title">PRACTICA VUE 3</h1>
    <h2 class="counter" :class="classCounter"> {{ count }} </h2>
  
<div class="buttons-container">
  <button class="increment" @click="increment">Aumentar</button>
  <button class="decrement" @click="decrement">Disminuir</button>
  <button class="reset" @click="reset">Resetear</button>
  <button class="add" @click="add" :disabled="bloquearBtnAdd">Add</button>
  <button class="delete" @click="del">Delete</button>
</div>

  <br>

  
  
  </div>

  <div>
    <ul>
      <li class="list-styles" v-for="(num, index) in numbers" :key="index">
        {{num}}
      </li>
    </ul>

  </div>

</template>



<style>


body {
  background-color: rgb(75, 75, 75);
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  transition: all 0.5s;
}

.title {
  position: relative;
  top: 70px;
}

/* buttons styles */
.counter {
  padding: 40px;
  font-size: 100px;
  width: 100px;
  text-align: center;
  justify-content: center;
  box-shadow: 17px 21px 45px -1px rgba(0,0,0,0.39);
-webkit-box-shadow: 17px 21px 45px -1px rgba(0,0,0,0.39);
-moz-box-shadow: 17px 21px 45px -1px rgba(0,0,0,0.39);
border-radius: 30px;
background-color: rgb(90, 89, 89);
}
.increment {
  background-color: rgb(47, 135, 66);
  border-radius: 10px 0 0 10px;
  font-weight: 700;
  color: gainsboro;
  border: none;
  padding: 20px;
  transition: all 0.5s;
}

.decrement {
  background-color: rgb(195, 47, 47);
  font-weight: 700;
  color: gainsboro;
  border: none;
  padding: 20px;
  transition: all 0.5s;
}

.reset {
  background-color: rgb(226, 226, 23);
  font-weight: 700;
  color: rgb(93, 94, 92);
  border: none;
  padding: 20px;
  transition: all 0.5s;
}
.add  {
  background-color: rgb(48, 48, 225);
  font-weight: 700;
  color: gainsboro;
  padding: 20px;
  border: none;
  transition: all 0.5s;
}

.delete {
  background-color: rgb(58, 56, 56);
  border-radius: 0 10px 10px 0px;
  font-weight: 700;
  color: gainsboro;
  border: none;
  padding: 20px;
  transition: all 0.5s;
}
.buttons-container {
  display: flex;
  align-content: center;
  flex-direction: row;
  justify-content: space-around;
  width: 200px;
  height: 100px;
  position: relative;
  top: 10px;
}


.main-section {
  width: 100vw;
  height: 50vh;
  background-color: rgb(216, 237, 243);
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.list-styles {
  margin: 20px;
  position: relative;
  top: 50px;
  color: whitesmoke;
  font-size: 30px;
  
}

.positive {
  color: rgb(149, 234, 59);
}

.negative {
  color: rgb(213, 60, 60);
}

.zero {
  color: rgb(250, 127, 5);
}

.buttons-container button:hover {
  padding: 0 40px;
  transition: all 0.5s;
}



</style>