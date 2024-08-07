<template>
    <span :class="['tag', { ativa }]">{{ tag }}</span>
</template>

<script lang="ts">
    export default {
        name: "TagIdentificacao",
        props: {
            tag: {
                type: String,
                required: true
            },
            ativa: Boolean
        }
    }
</script>

<style scoped>
    .tag {
        display: inline-block;
        border-radius: 0.5rem;
        min-width: 4.25rem;
        padding: 0.5rem;
        text-align: center;
        transition: 0.2s;
        font-weight: 400;
        color: var(--cinza);
        background: var(--cinza-claro);
    }

    .tag.ativa {
        color: var(--creme, #FFFAF3);
        background: var(--coral, #F0633C);
        font-weight: 700;
    }
</style>