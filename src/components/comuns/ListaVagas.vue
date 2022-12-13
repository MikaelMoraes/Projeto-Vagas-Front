<template>
    <div>
        <slot>  
        <div class="row mt-5" v-for="(vaga, index) in vagas " :key="index">
            <div class="col-12">
                <Vaga v-bind="vaga" />
            </div>
        </div>
        </slot>
    </div>
  
</template>
<script>
import Vaga from '@/components/comuns/Vaga.vue'
export default {
    name: 'ListaVaga',
    data:() =>({
        vagas:[]
    }),
    components: {
        Vaga
    },
    activated() {
        this.vagas = JSON.parse(localStorage.getItem('vagas'))
    },
    mounted() {
        this.emitter.on('filtrarVagas', vaga => {
            const vagas = JSON.parse(localStorage.getItem('vagas'))
            this.vagas = vagas.filter(reg => reg.titulo.toLowerCase().includes(vaga.titulo.toLowerCase()))
        })
    }
}
</script>
<style>

</style>