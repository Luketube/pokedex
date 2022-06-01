<template>
    <div class="card">
        <div class="informacoes">
            <div class="nome_id">
                <h2 class="nome">{{ dadosPokemon.name }}</h2>
                <p># {{ numeroDoPokemon +1 }}</p>
            </div>

            <p class="tipo"></p>
        </div>
        <hr class="linha_vertical">

        <div class="imagem">
            <img class="imagem_pokemon"
                v-bind:src="'https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/' + (numeroDoPokemon +1) + '.png'"
                alt="Imagem do pokemon">
        </div>

        <hr class="linha_vertical">
    </div>

</template>

<script>
export default {
    name: 'CardMenor',
    props: {
        numeroDoPokemon: {
            type: Number,
            required: true,
        },
    },
    data: function () {
        return {
            dadosPokemon: {},
            tipoPokemon: []
        }
    },
    methods: {
        async obtemDados() {
            const url = `https://pokeapi.co/api/v2/pokemon/${this.numeroDoPokemon +1}/`
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
        },
    },
    beforeMount(){
        this.obtemDados()
    }
   
}

</script>

<style scoped>
.card {
    align-items: center;
    display: flex;
    flex-direction: column;
    background-color: #FFB6C1;
    border: 1px solid #FFFFFF;
    border-radius: 25px;
    color: #FFFFFF;
    margin: 0 1rem;
    margin-bottom: 1rem;
    min-width: 235px;
    padding: 1rem;
    width: 20%;
}

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

.tipo {
    backdrop-filter: contrast(70%);
    border: 1px solid #ffffff;
    border-radius: 8px;
    font-size: 1rem;
    padding: .5rem;
    width: fit-content;
}

.linha_vertical {
    border: 1px solid #ffffff;
    width: 100%;
}

.imagem_pokemon {
    width: 155px;
}
</style>
