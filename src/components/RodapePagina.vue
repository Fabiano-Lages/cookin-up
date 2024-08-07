<template>
    <div id="rodape">
        <p>
            Desenvolvido por Alura | 2023 - Projeto fictício sem fins comerciais
        </p>
        <p>
            Reproduzido por <a href="https://github.com/Fabiano-Lages" target="_blank">Fabiano Teixeira Lages</a>
        </p>
    </div>
</template>

<script lang="ts">
    export default {
        name: 'RodapePagina'
    }
</script>

<style scoped>
    #rodape {
        background: var(--verde-escuro, #263A29);
        font-size: 1.125em;
        line-height: 150%; /* 1.6875em */
        align-items: center;
        display: flex;
        flex-direction: column;
        padding: 1.5rem;
    }

    a {
        text-decoration: none;
        color: var(--branco);
        font-weight: bold;
        transition-duration: .5s;
    }

    a:hover {
        color: var(--coral-claro);
    }
</style>