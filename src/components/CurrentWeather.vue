<script setup>
import moment from 'moment'
import { ref } from 'vue'

let mockData = {
  town: 'Tchikiland',
  temperature: 666,
  initialized: moment().format('LL')
}
let selectedCity = ref('')
let options = ref([
  { text: 'Rennes', value: 'Rennes' },
  { text: 'Tchikiland', value: 'Tchikiland' },
  { text: 'Truc', value: 'Truc' },
  { text: 'Bidule', value: 'Bidule' }
])

let weather = ref('22')
function refreshCurrentWeather() {
  weather.value = Math.floor(Math.random() * 60 - 30)
}
</script>

<template>
  <div class="blob">
    <div class="main-container">
      <h2>Où ?</h2>
      <select v-model="selectedCity" name="city" id="select-city">
        <option v-for="option in options" :value="option.value" :key="option.value">
          {{ option.text }}
        </option>
      </select>
      <button @click="refreshCurrentWeather" class="search-button">Search</button>
    </div>
    <div class="main-container">
      <h2 v-if="$route.params.city">Météo actuelle à {{ $route.params.city }}</h2>
      <h2 v-else>Météo Actuelle à {{ selectedCity }}</h2>
      <p>Température : {{ weather }}°C</p>
      <p>Date: {{ mockData.initialized }}</p>
    </div>
    <router-link v-if="$route.params.city" to="/" class="home-link">Retour à l'accueil</router-link>
  </div>
</template>

<style>
.blob {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.main-container {
  margin: auto;
  margin-top: 15px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: rgb(209, 209, 209);
  width: 80vw;
  height: 300px;
}

#select-city {
  width: 250px;
  height: 25px;
}

.search-button {
  margin-top: 10px;
  background-color: rgb(64, 64, 244);
  border-radius: 5px;
  border: none;
  color: white;
  text-align: center;
  width: 70px;
  height: 25px;
  cursor: pointer;
}

.home-link {
  text-decoration: none;
  margin-top: 10px;
  background-color: rgb(64, 64, 244);
  border-radius: 5px;
  border: none;
  color: white;
  text-align: center;
  width: 120px;
  height: 20px;
  padding: 5px;
  cursor: pointer;
}
</style>
