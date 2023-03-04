<template>
    <div class="container py-4">
        <div class="row">
            <div class="col">
                <PesquisarVaga />
            </div>
        </div>

        <!-- Template customizado ex1
        <ListaVagas v-slot:default="slotProps">
            <div v-for="(vaga, index) in slotProps.vagas" :key="index">
                <h4>{{ vaga.titulo }}</h4>
                <p>{{ vaga.descricao }}</p>
            </div>
        </ListaVagas> -->

        <!-- Template customizado ex2
        <ListaVagas>
            <template v-slot:titulo="slotProps">
                {{ slotProps.dadosTitulo.titulo }}
                <hr>
            </template>
            
            <template v-slot:default="slotProps">
                {{ slotProps.vagas }}
                <hr>
            </template>
            
            <template v-slot:rodape="slotProps">
                {{ slotProps.dadosRodape.rodape }}
                {{ slotProps.dadosRodape.paginacao }}
            </template>
        </ListaVagas> -->
        
        <!-- Template padrão -->
        <ListaVagas/>
        <div class="row mt-5">
            <div class="col-4">
                <indicador-comum titulo="Vagas abertas" indicador="100" bg="bg-dark" color="text-white"></indicador-comum>
            </div>
            <div class="col-4">
                <indicador-comum titulo="Profissionais cadastrados" indicador="210" bg="bg-dark"
                    color="text-white"></indicador-comum>
            </div>
            <div class="col-4">
                <indicador-comum titulo="Visitantes online" :indicador="usuariosOnline" bg="bg-light"
                    color="text-dark"></indicador-comum>
            </div>
        </div>
    </div>
</template>
  
<script>
import IndicadorComum from '../comuns/Indicador.vue';
import ListaVagas from '../comuns/ListaVagas.vue';
import PesquisarVaga from '../comuns/PesquisarVaga.vue'

export default {
    name: "HomePage",
    components: { PesquisarVaga, IndicadorComum, ListaVagas },
    data: () => ({
        usuariosOnline: 0,
    }),
    methods: {
        getUsuariosOnline() {
            this.usuariosOnline = Math.floor(Math.random() * 101) //entre 0 e 100
        }
    },
    created() {
        setInterval(this.getUsuariosOnline, 1000) //a cada 1s
    },
}
</script>
  
<style></style>  