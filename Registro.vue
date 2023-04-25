<template>
  <v-container fluid class="mt-15">
    <v-layout row justify-center>
      <v-flex xs12>
        <h1 class="blue--text text-xs-center" style="text-align: center;">CREA UNA CUENTA</h1>
      </v-flex>
    </v-layout>
    <v-layout row justify-center>
      <v-flex xs12 sm8 md6>
        <v-form v-model="valid" ref="form" style="border: 2px solid blue; padding: 24px;">
          <v-text-field label="Nombre Completo" v-model="name" required outlined></v-text-field>
          <v-text-field label="Matrícula" v-model="id" required outlined></v-text-field>
          <v-text-field v-if="error.length === 0" label="Correo Institucional" v-model="emailInstitutional" :rules="[reglas.emailRules]" required outlined></v-text-field>
          <v-text-field v-else label="Correo Institucional" @change="borrarerror" @keydown="borrarerror" v-model="emailInstitutional" :rules="[reglas.emailRules, error]" required outlined></v-text-field>
          <v-text-field label="Correo Personal" v-model="emailPersonal" :rules="[reglas.emailRules]" required outlined></v-text-field>
          <v-text-field label="Contraseña" v-model="password" :type="showPassword ? 'text' : 'password'" :rules="[reglas.passwordRules]" required outlined></v-text-field>
          <v-text-field label="Confirmar Contraseña" v-model="confirmPassword" :type="showPassword ? 'text' : 'password'" :rules="[reglas.confirmPasswordRules]" required outlined></v-text-field>
          <v-checkbox label="Mostrar contraseña" v-model="showPassword"></v-checkbox>
          <v-checkbox label="Acepto términos y condiciones" v-model="dummy"></v-checkbox>
          <v-btn  style="background-color: blue; color: white;" @click="submitForm">Registrarse</v-btn>
        </v-form>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import firebase from 'firebase/compat'
export default {
  data () {
    return {
      valid: false,
      name: '',
      id: '',
      emailInstitutional: '',
      emailPersonal: '',
      password: '',
      confirmPassword: '',
      showPassword: false,
      dummy: false,
      uid: '',
      error: '',
      reglas: {
        emailRules: value => /.+@.+\..+/.test(value) || 'Formato de correo no es reconocible',
        passwordRules: value => value.length >= 6 || 'Contraseña debe de tener mínimo 6 caracteres',
        confirmPasswordRules: value => this.password === value || 'Contraseña no coincide'
      }
    }
  },
  methods: {
    submitForm () {
      if (this.$refs.form.validate()) {
        // Valid form submitted
        this.register()
      }
    },
    async register () {
      try {
        await firebase.auth().createUserWithEmailAndPassword(this.emailInstitutional, this.password).then(() => {
          this.signIn()
        })
      } catch (e) {
        this.error = e.message
        if (this.error === 'Firebase: The email address is already in use by another account. (auth/email-already-in-use).') {
          this.error = 'Correo Institucional ya en uso'
        }
      }
    },
    async signIn () {
      await firebase.auth().signInWithEmailAndPassword(this.emailInstitutional, this.password).then(() => {
        this.uid = firebase.auth().currentUser.uid
        this.createuserdb(this.uid)
      })
    },
    async createuserdb (uid) {
      await firebase.firestore().collection('users').doc(uid).set({
        Nombre: this.name,
        Matricula: this.id,
        CorreoPesonal: this.emailPersonal
      }
      ).then(() => {
        this.$router.push('/home')
      })
    },
    borrarerror () {
      this.error = ''
    }
  }
}
</script>

<style scoped>
.v-form {
  margin-top: 24px;
}
</style>
