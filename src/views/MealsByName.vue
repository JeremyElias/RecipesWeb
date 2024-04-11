<template>
    <div class="p-8 pb-0">
        <h1 class="text-4xl font-bold mb-4 text-orange-500">Buscar Comida Por Nombre</h1>
    </div>
    <div class="p-x8 pb-3">
        <input type="text" class="rounder border-2 bg-white border-orange-500 focus:border-orange-500 w-full"
            placeholder="Buscar Comida" v-model="keyword" @change="searchMeals">
    </div>
    <Meals :meals="filteredMeals" />
</template>

<script setup>
import { onMounted, ref, computed } from 'vue';
import { useRoute } from 'vue-router';
import store from '../store';
import YoutubeButton from '../components/YoutubeButton.vue';
import MealItem from '../components/MealItem.vue';
import Meals from '../components/Meals.vue';

const route = useRoute();
const keyword = ref('');

// meals se mantiene como una variable computada
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
    if (keyword.value) {
        store.dispatch('searchMeals', keyword.value);
    } else {
        store.commit("setSearchedMeals", []);
    }
}

onMounted(() => {
    keyword.value = route.params.name;
    if (keyword.value) {
        searchMeals();
    }
});

// Filtrar las recetas en meals basadas en la palabra clave ingresada
const filteredMeals = computed(() => {
    return meals.value.filter(meal => {
        return meal.strMeal.toLowerCase().includes(keyword.value.toLowerCase());
    });
});
</script>