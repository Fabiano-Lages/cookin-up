<template>
  <Banner />
  <ConteudoPrincipal />
  <RodapePagina />
</template>

<script lang="ts">
  import Banner from './components/Banner.vue';
  import ConteudoPrincipal from './components/ConteudoPrincipal.vue';
  import RodapePagina from "./components/RodapePagina.vue"

  export default {
    name: 'App',
    components: {
      Banner, 
      ConteudoPrincipal,
      RodapePagina
    }
  };
</script>
<style scoped>

</style>