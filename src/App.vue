<template>
  <div id="app">
    <h1>
      Jogo da Forca
    </h1>

    <section v-if="tela === 'inicio'" id="inicio">

      <FormVue
        v-if="etapa === 'palavra'" 
        title="Defina uma Palavra"
        button="Próximo"
        :action="setPalavra"
      />

      <FormVue 
        v-if="etapa === 'dica'" 
        title="Dica"
        button="Iniciar"
        :action="setDica"
      />

    </section>

    <section v-if="tela === 'jogo'" id="jogo">
      <JogoView 
        :erros="erros"
        :palavra="palavra"
        :dica="dica"
        :verificarLetra="verificarLetra"
        :etapa="etapa"
        :letras="letras"
        :jogar="jogar"
        :jogarNovamente="jogarNovamente"
      /> 
    </section>

  </div>
</template>

<script>
import './css/global.css'
import FormVue from './components/FormVue.vue'
import JogoView from './components/JogoView.vue'

export default {
  name: 'App',
  data() {
    return {
      tela: 'inicio',
      etapa: 'palavra',
      palavra: '',
      dica: '',
      erros: 0,
      letras: []
    }
  },
  
  components: {
    FormVue,
    JogoView
  },

  methods: {
    setPalavra(palavra) {
      this.palavra = palavra
      this.etapa = 'dica'
    },
    
    setDica(dica) {
      this.dica = dica
      this.etapa = 'jogo'
      this.tela = 'jogo'
    },

    verificarLetra(letra) {
      return this.letras.find(item => item.toLowerCase() === letra.toLowerCase())
    },

    jogar(letra) {
      // Adiciona letra selecionada
      this.letras.push(letra);

      // Validar Erro
      this.verificarErros(letra)
    },

    verificarErros(letra) {
      // Validar Acerto
      if(this.palavra.toLocaleLowerCase().indexOf(letra.toLocaleLowerCase()) >= 0) {
        return this.verificarAcertos()
      }

      // Validar Erros
      this.erros++

      // Enforcar

      if(this.erros === 6) {
        this.etapa = 'enforcado'
      }
    },

    verificarAcertos() {
      let letrasUnicas = [...new Set(this.palavra.split(''))]
      
      if(letrasUnicas.length === (this.letras.length - this.erros)) {
        this.etapa = 'ganhador'
      }
    },

    jogarNovamente() {
      this.palavra = ''
      this.dica = ''
      this.erros = 0
      this.letras = []
      this.tela = 'inicio'
      this.etapa = 'palavra'
    }
  }
}
</script>

<style>
  #app {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
</style>
