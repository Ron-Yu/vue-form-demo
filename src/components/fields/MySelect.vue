<template>
  <section>
      <label>{{label}}</label>
      <select @change="updateValue($event.target.value)" class="browser-default">
        <option value="" disabled selected>{{label}}</option>
        <template v-for="option in options">
          <option :value="option">{{option}}</option>
        </template>
      </select>
  </section>
</template>

<script>
export default {
  model: {
    prop: 'checked',
    event: 'change'
  },
  props: {
    options: {
      type: Array,
      default: []
    },
    label: {
      type: String,
      default: 'select'
    }
  },
  methods: {
    updateValue(value) {
      this.$emit('change', value)
    }
  }
}
</script>

<style lang="scss">

</style>
