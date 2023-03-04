<template>
  <div>
    <VagasFavoritas />
    <Topo @navegar="componente = $event" />
    <AlertaComum v-if="exibirAlerta" :tipo="alerta.tipo">
      <template v-slot:titulo>
        <h5>{{ alerta.titulo }}</h5>
      </template>
      <p>{{ alerta.descricao }}</p>
    </AlertaComum>
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
    alerta: {titulo: '', descricao: '', tipo:''}
  }),
  mounted() {
    this.emitter.on('alerta', (a) => {
      this.alerta = a
      this.exibirAlerta = true
      setTimeout(() => this.exibirAlerta = false, 4000)
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
