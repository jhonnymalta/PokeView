<script setup>    
    import {useGetData} from '@/composition/getData';    

    const {data,getData,loading} = useGetData();
   
    getData('https://pokeapi.co/api/v2/pokemon');
</script>

<template>
    <div>
        <h2>Pokemons</h2>
        <p v-if="loading">Carregando informação..</p>
        <div v-if="data">
            <ul>
                <li v-for="(poke,index) in data.results" :key="index">
                    <router-link :to="`/pokeview/${poke.name}`">{{ poke.name }}</router-link>                    
                </li>
            </ul>
        </div>
    </div>
</template>