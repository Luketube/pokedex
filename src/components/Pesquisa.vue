<template>
    <nav class="campo_pesquisa">
        <input class="input_pesquisa" type="text" placeholder="Digite o nome do Pokemon">
        <button class="botao_pesquisa"><img src="../assets/lupa.png" alt="Icone de lupa"></button>
    </nav>

</template>

<script>
export default {
    name: 'PesquisaInput'
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
    background-color: #FFF5EE;
    border: none;
    border-radius: 100%;
}

</style>
