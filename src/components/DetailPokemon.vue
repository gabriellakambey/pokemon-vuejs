<template>
  <div class="row">
      <div class="col pokemon-name">
          <h1 class="text-center">{{name}}</h1>
          <div class="detail">Height: {{ height }}m</div>
          <div class="detail">Weight: {{ weight }}kg</div>
          <div class="detail types"
          v-for="(value, index) in pokemonTypes"
          :key="'value' + index">
              Pokemon Types: {{ value.type.name }}
          </div>
      </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
    name: 'PokemonDetails',
    props: ["selected"],
    data() {
        return {
            url: '',
            name: '',
            height: '',
            weight: '',
            pokemonTypes: []
        };
    },
    methods:{
        setDetail(data) {
            this.name = data.name,
            this.height = data.height/10,
            this.weight = data.weight/10,
            this.pokemonTypes = data.types
        }
    },
    watch: {
        selected:function(val) {
            if(val) {
                this.url = val;
            }
        },
        url: function (val) {
            if (val) {
                axios
                 .get(this.url)
                 .then((response) => this.setDetail(response.data))
                 .catch((error) => console.log(error));
            }
        }
    },
    mounted() {
        this.url = this.selected;
    }

}
</script>

<style>
.detail {
    padding-bottom: 10px;
    font-size: 20px;
    font-family:'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}
.row{
    
    font-size: 20px;
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}
</style>