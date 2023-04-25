<template>
  <div class="inicio">
    <h1>Información del Alumno</h1>
    <v-container>
      <v-row class="text-center">
        <v-col class="mb-4">
          <h1>.</h1>
          <h1 class="display-2 font-weight-bold mb-3" style="color: #384FFE;">
            INFORMACIÓN DEL ALUMNO
          </h1>
        </v-col>
        <v-col cols="12">
          <v-img
            src='https://www.sdpnoticias.com/resizer/3AQBn0Ve7SPMAJV8RK8CF4wosW8=/640x0/filters:format(png):quality(70)/cloudfront-us-east-1.images.arcpublishing.com/sdpnoticias/OJN7KYQI4BAWJPHYI7D7QZTJUU.png'
            class="my-3"
            contain
            height="200"
          />
        </v-col>
        <v-col class="mb-4">
          <div class="row">
            <div class="column" style="background-color:#ffff;width: 50%;">
              <!-- <h2>Column 1</h2> -->
              <h3 class="font-weight-bold mb-3" style="color: blue;">Nombre Completo</h3>
              <h4 v-row justify="right" style="color: #787C9D;">Juan Escutia</h4>
              <br>

              <h3 class="font-weight-bold mb-3" style="color: blue;">Correo Institucional</h3>
              <h4 v-row justify="right" style="color: #787C9D;">A01361234@tec.mx</h4>
              <br>

              <h3 class="font-weight-bold mb-3" style="color: blue;">Correo Personal </h3>
              <h4 v-row justify="right" style="color: #787C9D;">murioporlapatria@gmail.com</h4>
            </div>
            <div>
              <div class="column" style="background-color:#ffff;width: 600%;">
                <!-- <h2>Column 2</h2> -->
                <h3 class="font-weight-bold mb-3" style="color: blue;">Matricula </h3>
                <h4 v-row justify="right" style="color: #787C9D;">A01361234</h4>
                <br>

                <h3 class="font-weight-bold mb-3" style="color: blue;">Carrera </h3>
                <h4 v-row justify="right" style="color: #787C9D;">ISC</h4>
              </div>
            </div>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src
export default {
  name: 'Home'
}
</script>
