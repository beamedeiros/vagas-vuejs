<template>
  <div>
    {{ titulo }}
    <button @click="atualizarComponente()">Atualizar</button>
    <button @click="conteudo = 'home-page'">Home</button>
    <button @click="conteudo = 'publicar-vaga'">Publicar Vaga</button>
    <!-- renderizar de modo dinâmico os componentes home e publicar vaga -->
    <!-- <HomePage />
    <PublicarVaga /> -->
    <KeepAlive>
      <component :is="conteudo" />
    </KeepAlive>
  </div>
</template>
  
<script>
import HomePage from '@/components/views/HomePage.vue'
import PublicarVaga from '@/components/views/PublicarVaga.vue';
export default {
  name: 'ConteudoLayout',
  components: {
    HomePage,
    PublicarVaga
  },
  data: () => ({
    teste: 'O componente foi criado',
    titulo: 'componente conteudo',
    conteudo: 'home-page'
  }),
  methods: {
    atualizarComponente() {
      this.titulo += "*"
    }
  },
  // beforeCreate(){
  //   console.log('Antes de Criar', this.teste)
  // },
  // created() {
  //   console.log('Criado', this.teste)
  // },
  // beforeMount() {
  //   console.log('Antes de montar o template')
  // },
  // mounted() {
  //   console.log('Montado')
  // },
  // beforeUpdate() {
  //   console.log('Antes de atualizar')
  // },
  // updated() {
  //   console.log('Atualizado')
  // },
  // beforeUnmount() {
  //   console.log('Antes de desmontar')
  // },
  // unmounted(){
  //   console.log('Desmontado')
  // },
  // errorCaptured(){
  //   console.log('Erro capturado')
  // },
  // renderTracked() {
  //   console.log('Re-renderização rastreada')
  // },
  // renderTriggered() {
  //   console.log('Re-renderização acionada')
  // },

}
</script>
  
<style></style>
  