<template>

    <p class="tipo">{{ tipoPokemon }}</p>

</template>

<script>
export default{
    name: 'CardTipoMaior',
    props: {
        tipoPokemon: {
            type: String,
            required: true
        }
    }
}
</script>

<style scoped>
.tipo {
    backdrop-filter: contrast(70%);
    border: 1px solid #ffffff;
    border-radius: 8px;
    font-size: 2rem;
    letter-spacing: 0.25rem;
    margin-right: 1rem;
    padding: .5rem;
    width: fit-content;
}

</style>