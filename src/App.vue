<script setup>
import { ref } from 'vue'

const query = ref('Tel Aviv')
const activeCity = ref('Tel Aviv')

const weather = {
  temperature: 22,
  condition: 'Clear sky',
  windSpeed: 14,
  humidity: 62,
}

function searchWeather() {
  const city = query.value.trim()

  if (city) {
    activeCity.value = city
  }
}
</script>

<template>
  <main>
    <header>
      <p class="eyebrow">Weather Ops Dashboard</p>
      <h1>Local weather overview</h1>
      <p>Our first Vue screen. Weather values are mock data for now.</p>
    </header>

    <form @submit.prevent="searchWeather">
      <label for="city">City</label>
      <div class="search-row">
        <input id="city" v-model="query" placeholder="Enter a city" />
        <button type="submit">Check weather</button>
      </div>
    </form>

    <section class="weather-card" aria-live="polite">
      <p class="city">{{ activeCity }}</p>
      <p class="temperature">{{ weather.temperature }}°C</p>
      <p>{{ weather.condition }}</p>

      <dl>
        <div>
          <dt>Wind</dt>
          <dd>{{ weather.windSpeed }} km/h</dd>
        </div>
        <div>
          <dt>Humidity</dt>
          <dd>{{ weather.humidity }}%</dd>
        </div>
      </dl>
    </section>
  </main>
</template>