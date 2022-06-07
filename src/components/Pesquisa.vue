<template>
    <nav class="campo_pesquisa">
        <input v-model="pesquisa" class="input_pesquisa" type="text" placeholder="Digite o nome ou número do Pokemon">
        <button @click="obtemPesquisa" class="botao_pesquisa"><img src="../assets/lupa.png" alt="Icone de lupa"></button>
    </nav>

</template>

<script>
export default {
    name: 'PesquisaInput',
    data: function (){
        return{
            pesquisa: ''
        }
    },
    emits:[
        'buscaPokemon'
    ],
    methods: {
        obtemPesquisa(){
            this.$emit('buscaPokemon', this.pesquisa)
        }
    }
}


</script>

<style scoped>
.campo_pesquisa{
    align-items: center;
    background-color: #B22222;
    display: flex;
    justify-content:center;
    padding: 1rem;
}

.input_pesquisa{
    border: none;
    border-radius: 8px;
    padding: 0.5rem 1rem;
    margin-right: 1rem;
    width: 360px;
}

.botao_pesquisa{
    background-color: #FFFFFF;
    border: none;
    border-radius: 100%;
}

</style>
