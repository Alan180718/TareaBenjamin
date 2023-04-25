<template>
  <v-app>
    <div>
      <v-app-bar
        app
        color="blue"
        dark
      >
        <div class="d-flex align-center">
          <router-link to="/">
            <v-img
              alt="Tec Logo"
              class="shrink mr-2"
              contain
              src="https://javier.rodriguez.org.mx/itesm/2014/tecnologico-de-monterrey-blue.png"
              transition="scale-transition"
              width="100"
            />
          </router-link>
        </div>

        <v-spacer></v-spacer>
        <router-link to="inicio">
          <v-btn
            text
          >
            <span class="mr-2">INICIAR SESIÓN </span>
              <v-icon>mdi-open-in-new</v-icon>
          </v-btn>
        </router-link>
        <router-link to="/registro">
          <v-btn
            text
          >
            <span class="mr-2">REGISTRARSE</span>
            <v-icon>mdi-open-in-new</v-icon>
          </v-btn>
        </router-link>
      </v-app-bar>
    </div>
    <div>
      <router-view></router-view>
    </div>
  </v-app>
</template>

<script>
export default {
  name: 'VistaP'
}
</script>

<style scoped>

</style>
