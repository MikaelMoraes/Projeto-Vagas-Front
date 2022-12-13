<template>
  <div class="container py-4">
    <div class="row">
      <div class="col">
        <pesquisar-vaga></pesquisar-vaga>
      </div>
    </div>
    <ListaVagas />
    <div class="row mt-5">
      <div class="col-4">
        <indicador-vagas titulo="Vagas Abertas" :indicador="VagasA" bg="bg-dark" color="text-white"></indicador-vagas>
      </div>
      <div class="col-4">
        <indicador-vagas titulo="Profissionais Cadastrados" :indicador="Profissionais" bg="bg-dark" color="text-white"></indicador-vagas>
      </div>
      <div class="col-4">
        <indicador-vagas titulo="Visitantes Online" :indicador="usuariosOnline" bg="bg-light" color="text-dark"></indicador-vagas>
      </div>
    </div>
  </div>
</template>

<script>
import IndicadorVagas from '@/components/comuns/Indicador.vue'
import PesquisarVaga from '@/components/comuns/PesquisarVaga.vue'
import ListaVagas from '@/components/comuns/ListaVagas.vue'
export default{
  name: 'HomeMenu',
  components:{
    PesquisarVaga,
    IndicadorVagas,
    ListaVagas
  },
  data: () =>({
    VagasA: 100,
    Profissionais: 30,
    usuariosOnline: 0,
 
  }),
  methods:{
    getVagas(){
      this.Vagas = Math.floor(Math.random() * 101) //gera valor inteiro entre 0 e 100
    },
    getProfissionais(){
      this.Profissionais = Math.floor(Math.random() * 101) //gera valor inteiro entre 0 e 100
    },
    getUsuariosOnline(){
      this.usuariosOnline = Math.floor(Math.random() * 101) //gera valor inteiro entre 0 e 100
    }
  },
  created(){
    setInterval(this.getVagas, 10000),// cada 10 seg
    setInterval(this.getProfissionais, 50000),// cada 50 seg
    setInterval(this.getUsuariosOnline, 1000)// cada 1 seg
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >

</style>
