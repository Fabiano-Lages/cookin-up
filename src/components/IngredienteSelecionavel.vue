<template>
    <button class="ingrediente" @click="aoClicar" :aria-pressed="selecionado">
        <TagIdentificacao :tag="ingrediente" :ativa="selecionado" />
    </button>
</template>
<script lang="ts">
    import TagIdentificacao from './TagIdentificacao.vue';

    export default {
        name: "IngredienteSelecionavel",
        props: {
            ingrediente: {
                type: String,
                required: true
            }
        },
        data() {
            return {
                selecionado: false
            }
        },
        components: {
            TagIdentificacao
        },
        methods: {
            aoClicar() {
                this.selecionado = !this.selecionado;
                if(this.selecionado) {
                    this.$emit("adicionarIngrediente", this.ingrediente);
                } else {
                    this.$emit("removerIngrediente", this.ingrediente);
                }
            }
        },
        emits: ["adicionarIngrediente", "removerIngrediente"]
    };
</script>
<style scoped>
    .ingrediente {
        cursor:pointer;
    }
    
    .ingrediente:hover span {
        background: var(--verde-medio, #3D6D4A);
        color: var(--creme, #FFFAF3);
    }

</style>