<template>
  <div>
    <VagasFavoritas />
    <Topo @navegar="componente = $event" />
    <AlertaComum v-if="exibirAlerta">
      <h3>Teste 1: Slot Padrão</h3>
      <template v-slot:titulo>
        <h5>Título do alerta</h5>
      </template>
      <div>
        <p><strong>Teste 2: Slot Padrão</strong></p>
      </div>
      <template v-slot:descricao>
        <p>Desrição</p>
      </template>
      <ul>
        <li>Teste 3: Slot Padrão</li>
        <li>Teste 3: Slot Padrão</li>
        <li>Teste 3: Slot Padrão</li>
        <li>Teste 3: Slot Padrão</li>
      </ul>
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
