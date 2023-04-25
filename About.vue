<template>
  <div class="card-container">
    <div class="blue-title"><h1>MATERIAS INSCRITAS</h1></div>
    <div class="card">
      <div class="card-body">
        <div class="card-section">
          <h2 class="card-title blue--text">Título de la Materia</h2>
          <p class="grey--text">Profesor: Cristiano Ronaldo</p>
          <a href="#" class="card-link" @click="showDetails = true">Ver detalles</a>
        </div>
      </div>
    </div>
    <div class="blue-title"> </div>
    <div class="card">
      <div class="card-body">
        <div class="card-section">
          <h2 class="card-title blue--text">Título de la Materia</h2>
          <p class="grey--text">Profesor: Cristiano Ronaldo</p>
          <a href="#" class="card-link" @click="showDetails = true">Ver detalles</a>
        </div>
      </div>
    </div>
    <div class="blue-title"> </div>
    <div class="card">
      <div class="card-body">
        <div class="card-section">
          <h2 class="card-title blue--text">Título de la Materia</h2>
          <p class="grey--text">Profesor: Cristiano Ronaldo</p>
          <a href="#" class="card-link" @click="showDetails = true">Ver detalles</a>
        </div>
      </div>
    </div>
    <div class="blue-title"> </div>
    <div class="card">
      <div class="card-body">
        <div class="card-section">
          <h2 class="card-title blue--text">Título de la Materia</h2>
          <p class="grey--text">Profesor: Cristiano Ronaldo</p>
          <a href="#" class="card-link" @click="showDetails = true">Ver detalles</a>
        </div>
      </div>
    </div>
    <div class="blue-title"> </div>
    <div class="card">
      <div class="card-body">
        <div class="card-section">
          <h2 class="card-title blue--text">Título de la Materia</h2>
          <p class="grey--text">Profesor: Cristiano Ronaldo</p>
          <a href="#" class="card-link" @click="showDetails = true">Ver detalles</a>
        </div>
      </div>
    </div>
    <div class="blue-title"> </div>
    <div v-if="showDetails" class="card-overlay">
      <div class="card-overlay-content">
        <h2 class="card-title blue--text">Título de la Materia</h2>
        <p class="card-text grey--text">Profesor: Cristiano Ronaldo</p>
        <p class="card-text grey--text">Salón: La Congeladora</p>
        <p class="card-text grey--text">Días: Lunes, Miércoles & Viernes</p>
        <p class="card-text grey--text">Horario: 7:00 - 9:00</p>
        <a href="#" class="card-link" @click="showDetails = false">CERRAR</a>
      </div>
    </div>
  </div>
</template>

<style>
.card-container {
  margin: 80px auto;
  max-width: 800px; /* Ajusta el ancho de la tarjeta aquí */
}

.blue-title {
  color: blue;
  font-size: 24px;
  margin-bottom: 20px;
  text-align: center;
}

.card {
  background-color: white;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-shadow: 0 2px 2px rgba(0, 0, 0, 0.1);
  max-width: 10000px; /* Ajusta el ancho de la tarjeta aquí */
  padding: 3px;
}

.card-title {
  font-size: 18px;
  margin-bottom: 10px;
}

.card-section {
  margin-bottom: 20px;
}

.card-link {
  display: block;
  text-align: right;
}

.card-overlay {
  background-color: rgba(0,0,0,0.4);
  bottom: 0;
  left: 0;
  position: fixed;
  right: 0;
  top: 0;
  z-index: 999;
}

.card-overlay-content {
  background-color: white;
  border-radius: 4px;
  margin: auto;
  max-width: 400px;
  padding: 20px;
  position: center;
  top: 50%;
  transform: translateY(50%);
  width: 90%;
}

.card-text {
  font-size: 16px;
  line-height: 1.5;
  margin-bottom: 20px;
}
.card-container {
  margin: 80px auto;
}
</style>

<script>
export default {
  data () {
    return {
      showDetails: false
    }
  }
}
</script>
