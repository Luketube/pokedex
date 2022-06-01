<template>
  <header>

    <PesquisaInput />

  </header>

  <main>
    <CardMenor v-for="(pokemon, index) in listaPokemons" :key="index" :numeroDoPokemon="index"  />

  </main>


</template>

<script>
import PesquisaInput from './components/Pesquisa.vue';
import CardMenor from './components/CardMenor.vue';


export default {
  name: 'App',
  components: {
    PesquisaInput,
    CardMenor
  },
  data: function () {
    return {
      dados: {},
      totalPokemons: 3,
      //898 total de pokemons
      listaPokemons: [],
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
    obtemDadosPokemon(index){
      const url = `https://pokeapi.co/api/v2/pokemon/${index +1}/`
      const options = {
        method: 'GET',
        mode: 'cors',
        headers: {
          'content-type': 'application/json;charset=utf-8'
        }
      }

      fetch(url, options).then(
        response => response.json()
      ).then(
        data => {
          this.dadosPokemon = data;
        }
        
      )

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

main {
  padding-top: 5rem;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
