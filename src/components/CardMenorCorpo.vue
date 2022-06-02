<template>


    <div class="card" v-bind:class="elementoPokemon">
        <slot></slot>
    </div>


</template>

<script>
export default{
    name: 'CardMenorCorpo',
    props:{
        elementoPokemon:{
            type: String,
            required: true
        }
    }
}
</script>

<style scoped>
.card {
    align-items: center;
    display: flex;
    flex-direction: column;
    border: 1px solid #FFFFFF;
    border-radius: 25px;
    color: #FFFFFF;
    margin: 0 1rem;
    margin-bottom: 1rem;
    min-width: 235px;
    padding: 1rem;
    width: 20%;
}
.normal{
    background-color: #919AA2;
}
.fire{
    background-color: #F28D52;
}
.water{
    background-color: #5090D6;
}
.grass{
    background-color: #63BC5A;
}
.flying{
    background-color: #89AAE3;
}
.fighting{
    background-color: #CE416B;
}
.poison{
    background-color: #B567CE;
}
.electric{
    background-color: #F2C53D;
}
.ground{
    background-color: #D97845;
}
.rock{
    background-color: #C5B78C;
}
.psychic{
    background-color: #FA7179;
}
.ice{
    background-color: #73CEC0;
}
.bug{
    background-color: #91C12F;
}
.ghost{
    background-color: #5269AD;
}
.steel{
    background-color: #5A8EA2;
}
.dragon{
    background-color: #0B6DC3;
}
.dark{
    background-color: #5A5465;
}
.fairy{
    background-color: #EC8FE6;
}


</style>