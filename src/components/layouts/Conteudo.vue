<template>
  <div>
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
  props: {
    conteudo: {
      type: String,
      required: true
    }
  },
  components: {
    HomePage,
    PublicarVaga
  },
}
</script>
  
<style></style>
  