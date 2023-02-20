<script setup>
import { useFavoritosStore } from '../store/favoritos.js';
import { storeToRefs } from 'pinia';
import {RouterLink} from 'vue-router'

const useFavoritos = useFavoritosStore();

const {favoritos} = storeToRefs(useFavoritos);
const { remove } = useFavoritos;

</script>


<template>
    <h1>Favoritos</h1>
    <p v-if="favoritos.lenght === 0">Sin favoritos</p>
    <ul class="list-group" v-else>
        <li class="list-group-item"
        v-for="poke in favoritos"
        :key="poke.id"
        ><div>
            {{ poke.name }}
        </div>
        <div>
            <router-link :to="`/pokemons/${poke.name}`" class="btn btn-sm btn-primary me-2" @click="">Más información</router-link>
        </div>
        <div>
            <button class="btn btn-sm btn-danger" @click="remove(poke.id)">eliminar</button>
        </div>
        </li>
    </ul>
</template>