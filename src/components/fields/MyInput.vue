<template>
  <div class="row">
    <div class="input-field col s12">
      <input
        :autofocus="autofocus"
        :name="fieldName"
        :id="fieldName"
        :type="type"
        :value="value"
        v-validate="rules"
        @input="updateValue($event.target.value)"
        >
      <label :for="fieldName" >{{labelText}}</label>
      <p v-show="errors.has('email')" class="field-error">{{ errors.first('email') }}</p>
      <p v-show="errors.has('userName')" class="field-error">{{ errors.first('userName') }}</p>
      <p v-show="errors.has('password')" class="field-error">{{ errors.first('password') }}</p>
      <p v-show="errors.has('passwordConfirmation')" class="field-error">{{ errors.first('passwordConfirmation') }}</p>
    </div>
  </div>
</template>

<script>
import startCase from 'lodash/startCase'

const INI_PROPS = {
  autofocus: false,
  type: 'text',
  value: '',
  rules: () => ({})
}

export default {
  props: {
    autofocus: {
      type: Boolean,
      default: INI_PROPS.autofocus
    },
    fieldName: {
      type: String,
      required: true
    },
    type: {
      type: String,
      default: INI_PROPS.type
    },
    value: {
      type: String,
      default: INI_PROPS.value
    },
    rules: {
      type: Object,
      default: INI_PROPS.rules
    }
  },
  methods: {
    updateValue(value) {
      this.$emit('input', value)
    }
  },
  computed: {
    labelText() {
      return startCase(this.fieldName)
    }
  }
}
</script>

<style lang="scss">
  .field-error {
    margin-top: 0;
    color: #e53935;
  }
</style>
