<template>
  <VagasFavoritas/>
  <Topo @navegar="componente= $event"/>
  <Conteudo :conteudo="componente" />
</template>

<script>
import VagasFavoritas from './components/comuns/VagasFavoritas.vue';
import Conteudo from './components/layouts/Conteudo.vue';
import Topo from './components/layouts/Topo.vue';

export default {
  name: 'App',
  components: {
    Topo,
    Conteudo,
    VagasFavoritas
},
  data: () => ({
    componente: 'HomePage'
  }),
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
