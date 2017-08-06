<template>
  <p>
    <input
      type="checkbox"
      class="filled-in"
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
    checked: Boolean,
    value: String,
    fieldName: {
      type: String,
      required: true
    },
    label: {
      type: String,
      required: true
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
