<template>
    <section>
        {{ id }}
    </section>
</template>

<script>
import { getPoke } from '../services.js/service'
export default {
    name: 'PokemonCard',
    data(){
        return{
            pokeInf: {},

        }
    },
    methods:{
        async fetchInf() {
            const inf = await getPoke(this.id)
            console.log(inf)
        }
    },
    async created(){
        await this.methods.fetchInf()
    }, 
    props:{
        id: String
    }
}
</script>


<style scoped>

</style>