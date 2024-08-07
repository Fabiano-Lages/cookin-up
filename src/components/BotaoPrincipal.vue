<template>
    <button class="botao-busca">{{ valor }}</button>
</template>
<script lang="ts">
    export default {
        name: 'BotaoPrincipal',
        props: {
            valor: {
                type: String,
                required: true
            }
        }
    }
</script>

<style>
    .botao-busca {
        background-color: var(--coral);
        color: var(--creme);
        cursor: pointer;
        border-radius: 0.5rem;
        padding: .6rem 7.5rem;
        font-weight: bold;;
    }
</style>