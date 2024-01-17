<template>
  <div class="formulario">
    <div class="form-title">
      {{title}}
    </div>

    <input type="text" class="form-input" v-model="inputValue">

    <button 
    v-on:click="onSubmit"
    :disable="inputValue.length === 0">
      {{button}}
    </button>
  </div>
</template>

<script>
export default {
  name: 'FormVue',
  props: {
    title: String,
    button: String,
    action: Function
  },

  data() {
    return {
      inputValue:''
    }
  },

  methods: {
    onSubmit() {
      this.action(this.inputValue)
      this.inputValue = ''
    }
  }
}
</script>

<style scoped>
  .formulario {
    display: flex;
    flex-direction: column;
    text-align: center;
    align-items: center;
    justify-content: center;
    margin-top: 20px;
  }

  .form-input {
    padding: 10px 5px;
    border: 0;
    border-radius: 5px;
    margin: 10px 0;
    text-align: center;
    color: var(--color-text-dark);
    font-size: 1rem;
  }
</style>