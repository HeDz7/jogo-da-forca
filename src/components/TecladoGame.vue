<template>
  <div class="teclado">
    <button class="teclado-botao" 
      v-for="(letra, key) in 'abcdefghijklmnopqrstuvwxyz'"
      :key="key"
      :disabled="verificarLetra(letra)"
      @click="jogar(letra)"
    >
      {{ letra }}
    </button>
  </div>
</template>

<script>
export default {
  name: 'TecladoGame',
  props: {
    letras: Array,
    verificarLetra: Function,
    jogar: Function
  }
}
</script>

<style scoped>
  .teclado {
    max-width: 80%;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-content: center;
    column-gap: 1rem;
    row-gap: 1rem;
    margin-top: 1rem;
  }

  .teclado-botao {
    font-size: 1.5rem;
    text-transform: uppercase;
    cursor: pointer;
    transition: .2s ease-in-out;
  }

  .teclado-botao:hover {
    background-color: var(--color-text-title);
  }

</style>