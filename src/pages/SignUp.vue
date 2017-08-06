<template>
  <section class="row">
    <h5>Sign Up Form</h5>
    <form class="col s6">
      <MyInput fieldName="userName" :autofocus="true" v-model="signUpForm.userName" :rules="rules.userName"/>
      <MyInput fieldName="email" v-model="signUpForm.email" :rules="rules.email" />
      <MyInput fieldName="password" type="password" v-model="signUpForm.password" :rules="rules.password"/>
      <MyInput fieldName="passwordConfirmation" type="password" v-model="signUpForm.passwordConfirmation" :rules="rules.passwordConfirmation"/>
      
      
      <div class="row">
        <div class="col s12">
          <legend class="legend">Gender</legend>
          <template v-for="gender in genderOptions">
            <MyRadio
              fieldName="gender"
              v-model="signUpForm.gender"
              :label="gender"
              :value="gender"
              >
            </MyRadio>
          </template>
          <p class="field-error" v-show="errors.has('gender')">{{ errors.first('gender') }}</p>
        </div>
      </div>
                
      <div class="row">
        <div class="col s12">
          <legend class="legend">Color</legend>
          <template v-for="color in colorOptions">
            <MyCheckbox
              fieldName="color"
              :label="color"
              :value="color"
              v-model="signUpForm.color"
              >
            </MyCheckbox>
          </template>
        </div>
      </div>
      
      <div class="row">
        <div class="col s12">
          <MySelect
            label="Select Hobby"
            :options="hobbyOptions"
            v-model="signUpForm.hobby"
            >
          </MySelect>
        </div>
      </div>
      
      <MyButton :handleValidate="validateForm"></MyButton>
    </form>
    <section class="col s6">
      <p>userName: {{signUpForm.userName}}</p>
      <p>email: {{signUpForm.email}}</p>
      <p>password: {{signUpForm.password}}</p>
      <p>passwordConfirmation: {{signUpForm.passwordConfirmation}}</p>
      <p>gender: {{signUpForm.gender}}</p>
      <p>color: {{signUpForm.color}}</p>
      <p>hobby: {{signUpForm.hobby}}</p>
    </section>
  </section>
</template>

<script>
import MyButton from '../components/MyButton.vue'
import MyInput from '../components/fields/MyInput.vue'
import MyRadio from '../components/fields/MyRadio.vue'
import MyCheckbox from '../components/fields/MyCheckbox.vue'
import MySelect from '../components/fields/MySelect.vue'

export default {
  components: {
    MyButton,
    MyInput,
    MyRadio,
    MyCheckbox,
    MySelect
  },
  data() {
    return {
      genderOptions: ['male', 'female'],
      colorOptions: ['red', 'yellow', 'blue', 'green'],
      hobbyOptions: ['reading', 'fishing', 'playing'],
      signUpForm: {
        userName: '',
        email: '',
        password: '',
        passwordConfirmation: '',
        gender: '',
        color: [],
        hobby: ''
      },
      rules: {
        userName: { rules: { required: true, max: 12, min: 6 } },
        email: { rules: { required: true, email: true } },
        password: {
          rules: {
            required: true,
            max: 12,
            min: 6,
            confirmed: true
          }
        },
        passwordConfirmation: {
          rules: { required: true }
        },
        gender: {
          rules: { required: true }
        }
      },
      myErrors: []
    }
  },
  methods: {
    validateGenderField() {
      return this.signUpForm.gender.length !== 0
    },
    validateHobbyField() {
      return this.signUpForm.hobby.length !== 0
    },
    validateForm() {
      // console.log('validate')
      // if (this.validateGenderField()) {
      //   this.myErrors.push('gender')
      // }
      // this.validateHobbyField()
    }
  }
}
</script>

<style lang="scss">
  .legend {
    color: #9e9e9e;
    font-size: 1rem;
    transform: scale(0.8);
  }
</style>
