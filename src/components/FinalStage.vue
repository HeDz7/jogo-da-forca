<template>
  <div class="final">
    <div :class="`final-text ${etapa}`">
      {{texto}}
    </div>

    <button class="final-button"
      @click="jogarNovamente"
    >
      Jogar Novamente
    </button>
  </div>
</template>

<script>
export default {
  name: 'FinalStage',
  props: {
    etapa: String,
    texto: String,
    jogarNovamente: Function
  }
}
</script>

<style scoped>
  .final-text {
    margin: 20px 0;
    font-size: 2rem;
    font-weight: bold;
  }

  .final-text.enforcado {
    color: var(--color-text-error);
  }

    .final-text.ganhador {
    color: var(--color-text-success);
  }

</style>