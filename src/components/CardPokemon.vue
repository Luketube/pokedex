<template>
    <CardMenorCorpo :elementoPokemon="elementoPrincipal">
        <nav class="card_header">
            <button @click="voltarPagina" class="botao_voltar" v-bind:class="elementoPrincipal" ><img src="../assets/arrow.png" alt="Icone voltar"></button>
            <p class="index_pokemon"># {{ idPokemon }}</p>
        </nav>
        <div class="nome_tipo">
            <h2 class="nome_pokemon">{{ dadosPokemon.name }}</h2>
            <div class="tipo_pokemon">
                <CardTipoMaior v-for="(tipo, index) in dadosPokemon.types" :key="index" :tipoPokemon="dadosPokemon.types[index].type.name" />
            </div>
        </div>
        <hr class="linha_vertical">
        <img class="imagem_pokemon"
            v-bind:src="imagemPokemon"
            alt="Imagem do pokemon">
        <hr class="linha_vertical">
        <div class="informacoes">
            <div class="informacoes_linha">
                <p class="informacoes_fixo">Altura:</p>
                <p>{{ (parseInt(dadosPokemon.height) / 10).toFixed(2) }} m</p>
            </div>
            <div class="informacoes_linha">
                <p class="informacoes_fixo">Peso:</p>
                <p>{{ (parseInt(dadosPokemon.weight) / 10).toFixed(2) }} Kg</p>
            </div>
        </div>

    </CardMenorCorpo>

</template>

<script>
import CardMenorCorpo from './CardMenorCorpo.vue'
import CardTipoMaior from './CardTipoMaior.vue';
export default {
    name: "CardPokemon",
    components: {
    CardMenorCorpo,
    CardTipoMaior
},
    data: function () {
        return {
            dadosPokemon: {},
            elementoPrincipal: '',
            imagemPokemon: '',
            idPokemon: ''
        };
    },
    props: {
        pokemon:{
            type: String,
            required: true
        }
    },
    emits:[
        'voltar'
    ],
    methods: {
        obtemDadosPokemon(){
            const url = `https://pokeapi.co/api/v2/pokemon/${this.pokemon}`
            const options = {
                method: 'GET',
                mode: 'cors',
                headers: {
                    "content-type": "application/json;charset=utf-8"
                }
            };
            fetch(url, options).then(
                response => response.json()
            ).then(
                data => {
                    this.dadosPokemon = data;
                    this.elementoPrincipal = data.types[0].type.name;
                    this.imagemPokemon = data.sprites.front_default;
                    this.idPokemon = data.id;
                }
            )
        },
        voltarPagina(){
            this.$emit('voltar')
        }
    },
    beforeMount() {
        this.obtemDadosPokemon();
    }

}

</script>

<style>
.card {
    align-items: center;
    border: 2px solid #333333;
    border-radius: 16px;
    color: #ffffff;
    display: flex;
    flex-direction: column;
    padding: 1rem 2rem;
    width: 20%;
}

.card_header {
    align-items: center;
    display: flex;
    justify-content: space-between;
    width: 100%;
    margin-bottom: 1rem;
}

.botao_voltar{
    border: none;
}
.botao_voltar:hover {
    cursor: pointer;
}

.index_pokemon {
    font-size: 2rem;
}

.nome_tipo {
    width: 100%;
}

.nome_pokemon {
    font-size: 2.5rem;
    padding-bottom: .5rem;
}

.tipo_pokemon {
    display: flex;
}

.imagem_pokemon {
    width: 90%;
}

.linha_vertical {
    width: 100%;
    border: 1px solid #ffffff;
}

.informacoes {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    width: 100%;
}

.informacoes_fixo {
    width: 9rem;
}

.informacoes_linha {
    display: flex;
    padding: 0 0 1rem 1rem;
    font-size: 1.75rem;
}
</style>