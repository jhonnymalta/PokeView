<script setup>
import {useRoute,useRouter} from 'vue-router'
import {ref} from 'vue'
import {useGetData} from '@/composition/getData';    

const {data,getData,loading} = useGetData();


const route = useRoute()
const router = useRouter()
const back = ()=>{router.push('/pokemons')}


getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`)

</script>
<template>
    <div>
        <p v-if="loading">Carregando informação..</p>
    
        <h2>Eu escolho você: {{ route.params.name}}</h2>
        <div v-if="data">
            <h3>Altura: {{ data.height }}</h3>
            <h3>Peso: {{ data.weight }}</h3>
            <div>
                <img :src="data.sprites.front_default" alt="pokemon img">
            </div>
            <button @click="back">voltar</button>
        </div>
    </div>
</template>