<script setup>
import { ref, reactive } from 'vue';
const countries = reactive([
  {name:"Bangladesh", capital:"Dhaka"},
  {name:"Nepal", capital:"Kathmandu"},
  {name:"Bhutan", capital:"Thimphu"},
  {name:"Sri Lanka", capital:"Colombo"},
  {name:"India", capital:"New Delhi"},
  {name:"Pakistan", capital:"Islamabad"},
  {name:"Maldives", capital:"Male"}
]);
const capitalNames = countries.map(country => country.capital);

function getScore(){
 let score = 0;
 countries.forEach(country => {
  if(country.answer === country.capital){
    score++;
  }
 })
 return score;
}
</script>

<template>
  <section class="container mx-auto text-left max-w-screen-md py-20">
    <h1 class="text-4xl mb-10 text-center font-bold">Vue Quiz</h1>
   
    <p class="mb-3 text-red-600">Your Score: <span class="text-2xl font-bold">{{ getScore() }}</span></p>
    <div class="border border-gray-400 p-3 rounded bg-green-100 mb-3" v-for="(country, index) in countries" :key="index">
      <p class="mb-3 font-bold">What is the capital of {{ country.name }}?</p>
        <template v-for="(capital, index) in capitalNames" :key="index">
        <input type="radio" :value="capital" :name="country.name" v-model="country.answer">
        <label class="ml-1 mr-4">{{ capital }}</label>
        </template>
    </div>
  </section>
</template>

<style scoped>

</style>
