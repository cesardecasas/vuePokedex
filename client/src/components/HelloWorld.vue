<template>
  <div class="hello">
    <h1>{{ newMsg }}</h1>
    <h3 @click="counter">{{ count }}</h3>
    <ul>
      <li class="color" v-for="el in arr" v-bind:key="el.name">
        {{el.name}}
      </li>
    </ul>
    <h3>pokemon</h3>
    <button @click="fetchPokemon">get poke</button>
    <ul v-if="poke.length > 1">
      <li v-for="pokemon in poke" v-bind:key="pokemon.name">
        <pokemon-card :id="pokemon.url.split('pokemon/')[1].split('/')[0]"/>
      </li>
    </ul>
  </div>
</template>

<script>
import { getPokes } from '../services.js/service'
import PokemonCard from './PokemonCard.vue'
export default {
  components: { PokemonCard },
  name: 'HelloWorld',
  data(){
    return{
      newMsg:'my first vue page', 
      count: 1,
      arr: [{name:'a'},{ name:'b'},{ name:'c'}, {name:'d'}],
      poke:[]
    }
  },
  methods: {
    counter() {
      this.count++
    }, 
    async fetchPokemon() {
      const n = await getPokes(5,1)

      this.poke = n.results
    }
  }, 
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
  display: inline;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.color{
  color: blueviolet;
}
</style>
