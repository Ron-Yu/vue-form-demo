<template>
  <section class="container">
    <SignUp></SignUp>
  </section>
</template>

<script>
import SignUp from './pages/SignUp.vue'

export default {
  components: {
    SignUp
  }
}
</script>

<style lang="scss">
  .container {
    width: 60%
  }
</style>
