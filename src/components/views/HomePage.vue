<template>
    <div class="container py-4">
        <div class="row">
            <div class="col">
                <PesquisarVaga />
            </div>
        </div>

        <div class="row mt-5" v-for="(vaga, index) in vagas" :key="index">
            <div class="col">
                <VagaComum v-bind="vaga" />
            </div>
        </div>
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
import PesquisarVaga from '../comuns/PesquisarVaga.vue'
import VagaComum from '../comuns/Vaga.vue';

export default {
    name: "HomePage",
    components: { PesquisarVaga, IndicadorComum, VagaComum },
    data: () => ({
        usuariosOnline: 0,
        vagas: []
    }),
    methods: {
        getUsuariosOnline() {
            this.usuariosOnline = Math.floor(Math.random() * 101) //entre 0 e 100
        }
    },
    created() {
        setInterval(this.getUsuariosOnline, 1000) //a cada 1s
    },
    activated() {
        this.vagas = JSON.parse(localStorage.getItem('vagas'))
    },
    mounted() {
        this.emitter.on('filtrarVagas', vaga => {
            const vagas = JSON.parse(localStorage.getItem('vagas'))
            this.vagas  = vagas.filter(reg => reg.titulo.toLowerCase().includes(vaga.titulo.toLowerCase())) //true ou false: O método filter cria um novo array com todos os elementos que passaram no teste
        })
    }
}
</script>
  
<style></style>  