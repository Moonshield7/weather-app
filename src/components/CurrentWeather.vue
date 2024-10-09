<script setup>
import moment from 'moment'
import { ref } from 'vue'

let mockData = {
  town: 'Tchikiland',
  temperature: 666,
  initialized: moment().format('LL')
}

let options = ref([
  { value: 'Rennes' },
  { value: 'Tchikiland' },
  { value: 'Truc' },
  { value: 'Bidule' }
])
</script>

<template>
  <div class="main-container">
    <h2>Où ?</h2>
    <select v-model="selectedCity" name="city" id="select-city">
      <option v-for="option in options" :value="option.value">{{ option.value }}</option>
    </select>
    <buttonc class="search-button">Search</buttonc>
  </div>
  <div class="main-container">
    <h2>Météo Actuelle à {{ selectedCity }}</h2>
    <p>Température : {{ mockData.temperature }}°C</p>
    <p>Date: {{ mockData.initialized }}</p>
  </div>
</template>

<style>
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
  color: white;
  padding: 5px;
  text-align: center;
  width: 70px;
  height: 20px;
}

/* h1 {
  color: red;
} */
</style>
