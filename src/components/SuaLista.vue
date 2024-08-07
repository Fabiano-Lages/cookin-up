<template>
    <section>
        <span class="subtitulo-lg sua-lista-texto">
            Sua lista:
        </span>
        <ul v-if="lstIngredientes.length" class="ingredientes-sua-lista">
            <li v-for="(ingrediente, indice) in lstIngredientes" :key="indice">
                <TagIdentificacao :tag="ingrediente" :ativa="true" />
            </li>
        </ul>
        <p v-else class="paragrafo lista-vazia">
            <img src="../assets/images/icones/lista-vazia.svg" alt="Ícone de pesquisa" />
            Sua lista está vazia, selecione ingredientes para iniciar.
        </p>
    </section>
</template>

<script lang="ts">
    import type { PropType } from 'vue';
    import TagIdentificacao from './TagIdentificacao.vue';

    export default {
        name: 'SuaLista',
        components: {
            TagIdentificacao
        },
        props: {
            lstIngredientes: {
                type: Object as PropType<string[]>,
                required: true
            }
        },
    };
</script>

<style scoped>
    .sua-lista-texto {
        color: var(--coral, #F0633C);
        display: block;
        text-align: center;
        margin-bottom: 1.5rem;
    }

    .ingredientes-sua-lista {
        display: flex;
        justify-content: center;
        gap: 1rem 1.5rem;
        flex-wrap: wrap;
    }

    .lista-vazia {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
        gap: 0.25rem;

        color: var(--coral, #F0633C);
        text-align: center;
    }
</style>