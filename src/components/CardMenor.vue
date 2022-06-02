<template>
    <CardMenorCorpo :elementoPokemon="tipoPokemon" >
        <div class="informacoes">
            <div class="nome_id">
                <h2 class="nome">{{ dadosPokemon.name }}</h2>
                <p># {{ numeroDoPokemon +1 }}</p>
            </div>
            <div class="tipos_pokemon">
                <CardTipo v-for="(tipo, index) in dadosPokemon.types" :key="index" :tipoPokemon="dadosPokemon.types[index].type.name" />
            </div>
            
        </div>
        <hr class="linha_vertical">

        <div class="imagem">
            <img class="imagem_pokemon"
                v-bind:src="'https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/' + (numeroDoPokemon +1) + '.png'"
                alt="Imagem do pokemon">
        </div>

        <hr class="linha_vertical">

    </CardMenorCorpo>

</template>

<script>
import CardTipo from './CardTipo.vue'
import CardMenorCorpo from './CardMenorCorpo.vue';

export default {
    name: "CardMenor",
    components: {
    CardTipo,
    CardMenorCorpo
},
    props: {
        numeroDoPokemon: {
            type: Number,
            required: true,
        },
    },
    data: function () {
        return {
            dadosPokemon: {},
            tipoPokemon: '',
        };
    },
    methods: {
        async obtemDados() {
            const url = `https://pokeapi.co/api/v2/pokemon/${this.numeroDoPokemon + 1}/`;
            const options = {
                method: "GET",
                mode: "cors",
                headers: {
                    "content-type": "application/json;charset=utf-8"
                }
            };
            fetch(url, options).then(response => response.json()).then(data => {
                this.dadosPokemon = data;
                this.tipoPokemon = data.types[0].type.name
                
            });
        },
    },
    beforeMount() {
        this.obtemDados();
    }
}

</script>

<style scoped>



.informacoes {
    width: 100%;
}

.nome_id {
    align-items: flex-start;
    display: flex;
    justify-content: space-between;
    width: 100%;
}

.nome {
    font-size: 1.5rem;
    padding-bottom: 1rem;
}

.tipos_pokemon{
    display: flex;
}

.linha_vertical {
    border: 1px solid #ffffff;
    width: 100%;
}

.imagem_pokemon {
    width: 155px;
}
</style>
