<template>
    <header class="bg-white shadow-md h-16 flex justify-between items-stretch">
        <router-link :to="{ name: 'home' }" class="inline-flex items-center h-full px-5 ps-2 text-orange-500 font-bold">
            Inicio
        </router-link>
        <div class="flex items-center gap-1">
            <router-link :to="{ name: 'byName' }"
                class="inline-flex items-center px-2 h-full transition-colors hover:bg-orange-500 hover:text-white">
                Buscar Comida
            </router-link>
            <router-link :to="{ name: 'byLetter' }"
                class="inline-flex items-center px-2 h-full transition-colors hover:bg-orange-500 hover:text-white">
                Buscar Por Letra
            </router-link>
            <router-link :to="{ name: 'ingredients' }"
                class="inline-flex items-center px-2 h-full transition-colors hover:bg-orange-500 hover:text-white">
                Comida Por Ingredientes
            </router-link>
        </div>
    </header>
</template>