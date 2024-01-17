<template>
  <div class="forca">
    <img :src="`https://raw.githubusercontent.com/william-costa/wdev-hangman-game-resources/master/images/hangman/${erros}.svg`" alt="">
  </div>
</template>

<script>
export default {
  name: 'ForcaDoll',
  props: {
    erros: Number
  }
}
</script>

<style scoped>
  .forca img {
    height: 100px;
  }

</style>