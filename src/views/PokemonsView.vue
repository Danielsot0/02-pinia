<script setup>
import {RouterLink} from 'vue-router';
import {useGetData} from '@/composables/getData';

const {getData, loading, data, errorData} = useGetData();

getData('https://pokeapi.co/api/v2/pokemon');

</script>

<template>
    <h1>Pokemons</h1>
    <p v-if="loading"> Cargando información...</p>
    <div class="alert alert-danger mt-2" v-if="errorData">{{ errorData }}</div>

    <div v-if="data">
        <ul class="list-group">
            <li v-for="poke in data.results" class="list-group-item">
                <RouterLink :to="`/pokemons/${poke.name}`">
                    {{poke.name}}
                </RouterLink>
                
            </li>
        </ul>
        <div class="mt-2">
            <button :disabled="!data.previous" class="btn btn-success me-2" @click="getData(data.previous)">Previous</button>
            <button :disabled="!data.next" class="btn btn-primary" @click="getData(data.next)">next</button>
        </div>
    </div>
</template>