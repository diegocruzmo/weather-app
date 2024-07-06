<template>
  <div class="flex flex-col flex-1 items-center">
    <div class="flex flex-col items-center text-white py-12">
      <h1 class="text-4xl mb-2">{{ route.params.city }}</h1>
      <p class="text-sm mb-12">
        {{ new Date().toDateString() }}
      </p>
      <p class="text-7xl mb-4">
        {{ Math.round(weatherData.data.main.temp - 273.5) }}°C
      </p>
      <p>
        Feels like
        {{ Math.round(weatherData.data.main.feels_like - 273.5) }} °C
      </p>
      <p class="capitalize">
        {{ weatherData.data.weather[0].description }}
      </p>
      <img
        class="w-[150px] h-auto"
        :src="`https://openweathermap.org/img/wn/${weatherData.data.weather[0].icon}@2x.png`"
        :alt="weatherData.data.weather[0].description"
      />
    </div>

    <hr class="border-white border-opacity-10 border w-full" />
  </div>
</template>

<script setup>
import { useRoute } from 'vue-router'
import axios from 'axios'

const API_KEY = '93ab70d9f8a3c5d282881327e00c2ac9'
const route = useRoute()

const getWeatherData = async () => {
  try {
    const weatherData = await axios.get(
      `https://api.openweathermap.org/data/2.5/weather?q=${route.params.city}&appid=${API_KEY}`
    )
    return weatherData
  } catch (error) {
    console.log(error)
  }
}

const weatherData = await getWeatherData()
</script>
