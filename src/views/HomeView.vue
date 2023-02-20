<script setup>
import { storeToRefs } from "pinia";
import { useCounterStore } from "../store/counter.js";

const useCounter = useCounterStore();

const { increment } = useCounter;
const {count, double} = storeToRefs(useCounter);

</script>

<template>
  <div>

    <h1> Home counter: {{ count }}</h1>
    <h2> double: {{ double }}</h2>
    <button @click="increment">Increment</button>
      
      
  </div>
  
  </template>
