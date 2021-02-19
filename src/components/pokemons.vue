<template>
<div class="container">
    <img src="../assets/pokemon.png" alt="Logo Pokemon"/>
    <h1>Pokemon's</h1>
    <SearchPokemon />
    <div class="columns">
        <div class="col-md-8 justify-content-center">
            <div class="row align-items-start" 
            @click="setDetail(pokemon.url)"
            v-for="pokemon in pokemons"
            :key="pokemon.name">
                <ListPokemon :pokemon="pokemon"/>
            </div>
        </div>
        <div class="col-md-4 align-items-center">
            <DetailPokemon v-if="show" :selected="selected"/>
        </div>
    </div>
</div>
</template>

<script>
import SearchPokemon from './SearchPokemon.vue';
import ListPokemon from './ListPokemon.vue';
import DetailPokemon from './DetailPokemon.vue';
import axios from "axios";

export default {
    name: "Pokemons",
    components: {
        SearchPokemon,
        ListPokemon,
        DetailPokemon
    },
    data() {
        return {
            pokemons: [],
            selected: '',
            show: false
        }
    },
    methods: {
        setPokemon(data) {
            this.pokemons = data.results;
        },
        setDetail(url) {
            this.selected = url;
            this.show = true;
        }

    },
    mounted() {
        axios
            .get("https://pokeapi.co/api/v2/pokemon/")
            .then((response) => this.setPokemon(response.data))
            .catch((error) => console.log(error))
    }
}
</script>

<style scoped>
.container{
    /* font-family: Avenir, Helvetica, Arial, sans-serif; */
    text-align: center;
    margin-top: 60px;
    margin-bottom: 50px;
}

.columns{
  display: flex;
  justify-content: space-around;
}
</style>