<template>
  <p>
    <input
      type="radio"
      class="with-gap"
      :name="fieldName" 
      :id="label"
      :value="value"
      @change="updateValue($event.target.value)"
      />
    <label :for="label">{{label}}</label>
  </p>
</template>

<script>
export default {
  model: {
    prop: 'checked',
    event: 'change'
  },
  props: {
    value: String,
    fieldName: {
      type: String,
      required: true
    },
    label: {
      type: String,
      required: true
    },
    rules: {
      type: Object,
      default: () => ({})
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
