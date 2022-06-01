<template>

<div class="card">
    <nav class="card_header">
        <button class="botao_voltar"><img src="../assets/arrow.png" alt="Icone voltar"></button>
        <p class="index_pokemon">#35</p>
    </nav>
    <div class="nome_tipo">
        <h2 class="nome_pokemon">Clefairy</h2>
        <p class="tipo_pokemon">Fada</p>
    </div>
    <hr class="linha_vertical">
    <img class="imagem_pokemon" src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/35.png" alt="Imagem do pokemon">
    <hr class="linha_vertical">
    <div class="informacoes">
        <div class="informacoes_linha">
            <p class="informacoes_fixo">Altura:</p> 
            <p>182,88</p>
        </div>
        <div class="informacoes_linha">
            <p class="informacoes_fixo">Peso:</p>
            <p>75 Kg</p>
        </div>
    </div>
</div>

</template>

<script>
export default {
    name: 'CardPokemon'
}

</script>

<style scoped>
.card{
    align-items: center;
    background-color: #FFB6C1;
    border: 2px solid #333333;
    border-radius: 16px;
    color: #ffffff;
    display: flex;
    flex-direction: column;
    padding: 1rem 2rem;
    width: 20%;
}

.card_header{
    align-items: center;
    display: flex;
    justify-content: space-between;
    width: 100%;
    margin-bottom: 1rem;
}

.botao_voltar{
    border: none;
    background-color: #FFB6C1;
}
.botao_voltar:hover{
    cursor: pointer;
}

.index_pokemon{
    font-size: 2rem;
}

.nome_tipo{
    width: 100%;
}

.nome_pokemon{
    font-size: 2rem;
    padding-bottom: .5rem;
}

.tipo_pokemon{
    backdrop-filter: contrast(70%);
    border: 1px solid #ffffff;
    border-radius: 8px;
    font-size: 1.5rem;
    padding: .5rem;
    width: fit-content;
    
}

.imagem_pokemon{
    width: 90%;
}

.linha_vertical{
    width: 100%;
    border: 1px solid #ffffff;
}

.informacoes{
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    width: 100%;
}

.informacoes_fixo{
    width: 9rem;
}

.informacoes_linha{
    display: flex;
    padding: 0 0 1rem 1rem;
    font-size: 1.75rem;
}

</style>