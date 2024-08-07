<template>
    <main class="conteudo-principal">
        <SuaLista v-if="conteudo === 'SelecionarIngredientes'" :lstIngredientes="lstIngredientes" />

        <KeepAlive include="SelecaoIngredientes">
            <SelecaoIngredientes  v-if="conteudo === 'SelecionarIngredientes'"
                @adicionarIngrediente="adicionaIngrediente" 
                @removerIngrediente="removeIngrediente" 
                @buscarReceitas="navegar('MostrarReceitas')"
            />

            <MostrarReceitas  v-else-if="conteudo === 'MostrarReceitas'" 
                :lstIngredientes="lstIngredientes"
                @selecionarIngredientes="navegar('SelecionarIngredientes')"
            />
        </KeepAlive>
    </main>
</template>

<script lang="ts">
    import MostrarReceitas from './MostrarReceitas.vue';
    import SelecaoIngredientes from './SelecaoIngredientes.vue';
    import SuaLista from './SuaLista.vue';
    type Pagina = "SelecionarIngredientes" | "MostrarReceitas";

    export default {
        name: 'ConteudoPrincipal',
        data() {
            return ({
                lstIngredientes: [] as string[],
                conteudo: "SelecionarIngredientes" as Pagina
            })
        },
        methods: {
            adicionaIngrediente(ingrediente: string) {
                this.lstIngredientes.push(ingrediente);
            },
            removeIngrediente(ingrediente: string) {
                this.lstIngredientes = this.lstIngredientes.filter(item => item !== ingrediente);
            },
            navegar(pagina: Pagina) {
                this.conteudo = pagina;
            }
        },
        components: {
            SelecaoIngredientes, SuaLista, MostrarReceitas
        },
    }
</script>

<style scoped>
    .conteudo-principal {
        padding: 6.5rem 7.5rem;
        border-radius: 3.75rem 3.75rem 0rem 0rem;
        background: var(--creme, #FFFAF3);
        color: var(--cinza, #444);

        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 5rem;
    }

    @media only screen and (max-width: 1300px) {
        .conteudo-principal {
            padding: 5rem 3.75rem;
            gap: 3.5rem;
        }
    }

    @media only screen and (max-width: 767px) {
        .conteudo-principal {
            padding: 4rem 1.5rem;
            gap: 4rem;
        }
    }
</style>