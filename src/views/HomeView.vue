<template>
  <main class="container text-white">
    <div class="pt-4 mb-8 relative">
      <input
        type="text"
        v-model="searchQuery"
        placeholder="Search for a city..."
        class="py-2 px-1 w-full bg-transparent border-b focus:border-weather-secondary focus:outline-none"
      />
      <button
        class="bg-weather-secondary hover:bg-white hover:text-weather-primary text-white font-bold py-2 px-4 my-4 rounded"
        @click="handleClick"
      >
        Send
      </button>
    </div>
  </main>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const searchQuery = ref('')
const router = useRouter()

const handleClick = () => {
  router.push({
    name: 'cityView',
    params: { city: searchQuery.value }
  })
}
</script>
