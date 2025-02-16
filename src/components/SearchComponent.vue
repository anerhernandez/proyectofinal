<script>
import { defineProps } from 'vue';

async function searchapi(tipo){
    // document.getElementById("loading").textContent = "Loading API"
    let weapons = []
    await fetch(`https://mhw-db.com/weapons?q={"type":"${tipo}"}`)
    .then((resp) => resp.json())
    .then(function (data) {
            // document.getElementById("loading").textContent = "API loaded"
            weapons = data
        })
        .catch(function (error) {
            console.log(error);
        });
        return weapons
}
async function buscar(){
    let data = await searchapi("great-sword")
    return data
}
async function render(){
    let weapons = await buscar()
    console.log(weapons)
}
render()
</script>

<template> 
    <div>
        <h1>Search Component</h1>
        <!-- <button v-on:click="render()">Buscar</button> -->
        <!-- <div id="loading"></div> -->
    </div>
    Componente
</template>