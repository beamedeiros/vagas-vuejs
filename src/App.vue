<template>
  <div>
    <VagasFavoritas />
    <Topo @navegar="componente = $event" />
    <AlertaComum v-if="exibirAlerta"/>
    <Conteudo :conteudo="componente" />
  </div>
</template>

<script>
import AlertaComum from './components/comuns/Alerta.vue';
import VagasFavoritas from './components/comuns/VagasFavoritas.vue';
import Conteudo from './components/layouts/Conteudo.vue';
import Topo from './components/layouts/Topo.vue';

export default {
  name: 'App',
  components: {
    Topo,
    Conteudo,
    VagasFavoritas,
    AlertaComum
  },
  data: () => ({
    componente: 'HomePage',
    exibirAlerta: false,
  }),
  mounted() {
    this.emitter.on('alerta', () => {
      this.exibirAlerta = true
      setTimeout(() => this.exibirAlerta = false, 4000)
      console.log('Apresentar alerta')
    })
  }
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
