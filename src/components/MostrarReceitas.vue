<template>
    <section class="selecionar-ingredientes">
        <h1 class="cabecalho titulo-receitas">Receitas</h1>

        <p class="paragrafo-lg instrucoes">
            Resultados encontrados: {{ receitasEncontradas.length }}
        </p>

        <p class="paragrafo-lg instrucoes" v-if="receitasEncontradas.length > 0">
            Veja as opções de receitas que encontramos com os ingredientes que você escolheu.
        </p>

        <p class="paragrafo-lg vazio" v-else>
            <span>Ops, não encontramos resultados para sua combinação. Vamos tentar de novo?</span>
            <img src="@/assets/images/sem-receitas.png" alt="Não encontramos receitas">
        </p>

        <ul class="receitas">
            <li v-for="(item, indice) in receitasEncontradas" :key="indice">
                <CardReceita 
                    :receita="item" 
                />
            </li>
        </ul>

        <BotaoPrincipal :valor="'Editar lista'" @click="$emit('selecionarIngredientes')" />
    </section>
</template>

<script lang="ts">
    import { obterReceitas } from '@/http';
    import BotaoPrincipal from './BotaoPrincipal.vue';
    import type IReceita from '../interfaces/IReceita';
    import CardReceita from './CardReceita.vue';
    import type { PropType } from 'vue';
    
    export default {
        name: "MostrarReceitas",
        emits: ["selecionarIngredientes"],    
        props: {
            lstIngredientes: {
                type: Object as PropType<string[]>,
                required: true
            }
        },
        data() {
            return({
                receitasEncontradas: [] as IReceita[]
            });
        },
        components: {
            BotaoPrincipal, CardReceita
        },

        async created() {
            const receitas:IReceita[] = await obterReceitas();

            this.receitasEncontradas = receitas.filter(receita => receita.ingredientes.every(ingrediente => this.lstIngredientes.includes(ingrediente)));
        }
    }
</script>

<style>
    .titulo-receitas {
        color: var(--verde-medio, #3D6D4A);
        display: block;
        margin-bottom: 1.5rem;
    }

    .instrucoes {
        margin-bottom: 2rem;
    }

    .selecionar-ingredientes {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .receitas {
        margin-bottom: 1rem;
        display: flex;
        justify-content: center;
        gap: 1.5rem;
        flex-wrap: wrap;
    }

    .vazio {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 0.25rem
    }
</style>