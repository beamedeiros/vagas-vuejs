<template>
    <!-- <slot name="titulo" :dadosTitulo="{titulo: 'Título Lista', numVagas: 15}">
        <p>Título da lista de vagas</p>
    </slot> -->
    
    <slot :vagas="vagas">
        <div class="row mt-5" v-for="(vaga, index) in vagas" :key="index">
            <div class="col">
                <VagaComum v-bind="vaga" />
            </div>
        </div>
    </slot>

    <!-- <slot name="rodape" :dadosRodape="{titulo: 'Rodapé Lista', paginacao: {numPag: 10, pagAtual: 1}}">
        <p>Rodapé</p>
    </slot> -->
</template>

<script>
import VagaComum from '../comuns/Vaga.vue';
export default {
    name: "ListaVagas",
    data: () => ({
        vagas: []
    }),
    components: { VagaComum },
    activated() {
        this.vagas = JSON.parse(localStorage.getItem('vagas'))
    },
    mounted() {
        this.emitter.on('filtrarVagas', vaga => {
            const vagas = JSON.parse(localStorage.getItem('vagas'))
            this.vagas = vagas.filter(reg => reg.titulo.toLowerCase().includes(vaga.titulo.toLowerCase())) //true ou false: O método filter cria um novo array com todos os elementos que passaram no teste
        })
    }
}
</script>