<template>
  <v-container fluid class="mt-15">
    <v-layout row justify-center>
      <v-flex xs12>
        <h1 class="blue--text text-xs-center" style="text-align: center;">INICIO DE SESIÓN</h1>
      </v-flex>
    </v-layout>
    <v-layout row justify-center>
      <v-flex xs12 sm8 md6>
        <v-form v-model="valid" ref="form" style="border: 2px solid blue; padding: 24px;">
          <v-text-field v-if="errorcor.length === 0" label="Correo Institucional" v-model="emailInstitutional" :rules="[reglas.emailRules]" required outlined></v-text-field>
          <v-text-field v-else label="Correo Institucional" v-model="emailInstitutional" :rules="[reglas.emailRules, errorcor]" required outlined></v-text-field>
          <v-text-field v-if="errorcon.length === 0" label="Contraseña" v-model="password" :type="showPassword ? 'text' : 'password'" :rules="[reglas.passwordRules]" required outlined></v-text-field>
          <v-text-field v-else label="Contraseña" v-model="password" :type="showPassword ? 'text' : 'password'" :rules="[reglas.passwordRules, errorcon]" required outlined></v-text-field>
          <v-btn  style="background-color: blue; color: white;" @click="submitForm">Iniciar Sesión</v-btn>
        </v-form>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import firebase from 'firebase/compat'
export default {
  name: 'Inicio',
  data () {
    return {
      valid: false,
      emailInstitutional: '',
      password: '',
      showPassword: false,
      dummy: false,
      errorcor: '',
      errorcon: '',
      reglas: {
        emailRules: value => /.+@.+\..+/.test(value) || 'Formato de correo no es reconocible',
        passwordRules: value => value.length >= 6 || 'Contraseña debe de tener mínimo 6 caracteres'
      }
    }
  },
  methods: {
    submitForm () {
      if (this.$refs.form.validate()) {
        // Valid form submitted
        this.LogIn()
      }
    },
    async LogIn () {
      try {
        await firebase.auth().signInWithEmailAndPassword(this.emailInstitutional, this.password).then(() => {
          this.$router.push('/home')
        })
      } catch (e) {
        this.errorcor = e.message
        this.errorcon = e.message
        if (this.errorcor === 'Firebase: The email address is badly formatted. (auth/invalid-email).') {
          this.errorcor = 'El correo esta mal escrito'
        }
        if (this.errorcor === 'Firebase: There is no user record corresponding to this identifier. The user may have been deleted. (auth/user-not-found).') {
          this.errorcor = 'El correo no esta registrado'
        }
        if (this.errorcon === 'Firebase: A non-empty password must be provided (auth/missing-password).') {
          this.errorcon = 'Contraseña vacía'
        }
        if (this.errorcon === 'Firebase: The password is invalid or the user does not have a password. (auth/wrong-password).') {
          this.errorcon = 'Contraseña incorrecta'
        }
      }
    }
  }
}
</script>

<style scoped>
.v-form {
  margin-top: 24px;
}
</style>
