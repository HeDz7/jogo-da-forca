<template>
  <div class="jogo">
    <ForcaDoll 
      :erros="erros"
    />

    <PalavraView 
      :palavra="palavra"
      :dica="dica"
      :verificarLetra="verificarLetra"
      :etapa="etapa"
    />

    <TecladoGame 
      v-if="etapa === 'jogo'"
      :letras="letras"
      :verificarLetra="verificarLetra"
      :jogar="jogar"
    />

    <FinalStage 
      v-if="etapa != 'jogo'"
      :etapa="etapa"
      :texto="etapa === 'ganhador' ? 'Parabéns!' : 'Tente novamente!'"
      :jogarNovamente="jogarNovamente"
    />
  </div>
</template>

<script>
import ForcaDoll from './ForcaDoll.vue'
import PalavraView from './PalavraView.vue'
import TecladoGame from './TecladoGame.vue'
import FinalStage from './FinalStage.vue'

export default {
  name: 'JogoView',
  components: {
    ForcaDoll,
    PalavraView,
    TecladoGame,
    FinalStage
  },

  props: {
    erros: Number,
    palavra: String,
    dica: String,
    verificarLetra: Function,
    etapa: String,
    letras: Array,
    jogar: Function,
    jogarNovamente: Function
  },
}
</script>

<style scoped>
    .jogo {
      widows: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
    }

</style>