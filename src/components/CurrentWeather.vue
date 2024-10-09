<script setup>
import moment from 'moment'
import { ref } from 'vue'

let mockData = {
  town: 'Tchikiland',
  temperature: 666,
  initialized: moment().format('LL')
}
let selectedCity = ref('Rennes')
let options = ref([
  { text: 'Rennes', value: 'Rennes' },
  { text: 'Tchikiland', value: 'Tchikiland' },
  { text: 'Truc', value: 'Truc' },
  { text: 'Bidule', value: 'Bidule' }
])
</script>

<template>
  <div class="main-container">
    <h2>Où ?</h2>
    <select v-model="selectedCity" name="city" id="select-city">
      <option v-for="option in options" :value="option.value" :key="option.value">
        {{ option.text }}
      </option>
    </select>
    <button class="search-button">Search</button>
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
  border: none;
  color: white;
  /* padding: 5px; */
  text-align: center;
  width: 70px;
  height: 25px;
  cursor: pointer;
}

/* h1 {
  color: red;
} */
</style>
