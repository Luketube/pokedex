<template>
  <header>

    <PesquisaInput @buscaPokemon="pesquisaPokemon" />

  </header>

  <main>
    <div class="cards_pokemon" v-if="!pesquisaAtiva">
      <CardMenor v-for="(pokemon, index) in listaPokemons" :key="index" :numeroDoPokemon="index" />
    </div>

    <div class="cards_pokemon" v-if="pesquisaAtiva">
        <CardPokemon @voltar="reinicia" :idPokemon="numeroPokemon" />
    </div>
    
  

    
  </main>


</template>

<script>
import PesquisaInput from './components/Pesquisa.vue';
import CardMenor from './components/CardMenor.vue';
import CardPokemon from './components/CardPokemon.vue';

export default {
  name: 'App',
  components: {
    PesquisaInput,
    CardMenor,
    CardPokemon
},
  data: function () {
    return {
      dados: {},
      totalPokemons: 6,
      //898 total de pokemons
      listaPokemons: [],
      pesquisaAtiva: false,
      numeroPokemon: ''
    }
  },
  methods: {
    obtemTotalPokemons() {
      const url = 'https://pokeapi.co/api/v2/pokemon/'
      const options = {
        method: 'GET',
        mode: 'cors',
        headers: {
          'content-type': 'application/json;charset=utf-8'
        }
      }

      fetch(url, options)
        .then(
          response => response.json()
        )
        .then(
          data => {
            this.dados = data;

            for (var i = 0; i < this.totalPokemons; i++) {

              this.listaPokemons.push(this.dados.results[i]);
            }
          }
        );
    },
    pesquisaPokemon(informacao){
  
      this.numeroPokemon = informacao;
      this.pesquisaAtiva = true;
    },
    reinicia(){
      this.pesquisaAtiva = false;
    }
  },
  beforeMount() {
    this.obtemTotalPokemons()
  }
}

</script>

<style>
:root {
  background-color: #FFF5EE;
}

.cards_pokemon {
  padding-top: 5rem;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
