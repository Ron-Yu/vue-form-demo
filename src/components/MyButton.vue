<template>
  <button
    class="btn waves-effect waves-light myButton"
    @click.prevent="handleValidate"
    >
    {{text}}
    <i class="material-icons right">send</i>
  </button>
</template>

<script>
const INI_PROPS = {
  text: 'submit',
  handleValidate: () => {}
}

export default {
  props: {
    text: {
      type: String,
      default: INI_PROPS.text
    },
    handleValidate: {
      type: Function,
      default: INI_PROPS.handleValidate
    }
  }
}
</script>

<style lang="scss">

</style>
