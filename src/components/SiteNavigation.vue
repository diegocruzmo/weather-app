<template>
  <header class="sticky top-0 bg-weather-primary shadow-lg">
    <nav
      class="container flex flex-col justify-between sm:flex-row items-center gap-4 text-white py-6"
    >
      <router-link :to="{ name: 'home' }">
        <div class="flex items-center gap-3">
          <i class="fa-solid fa-sun text-2xl"></i>
          <p class="text-2xl">The Local Weather</p>
        </div>
      </router-link>

      <div class="flex gap-3">
        <i
          class="fa-solid fa-circle-info text-xl hover:text-weather-secondary duration-150 cursor-pointer"
          @click="toggleModal"
        ></i>
      </div>
      <BaseModal :modal-active="modalActive" @close-modal="toggleModal">
        <div class="text-black">
          <h1 class="text-2xl mb-1">About:</h1>
          <p class="mb-4">
            The Local Weather App allows you to track the weather
          </p>
        </div>
      </BaseModal>
    </nav>
  </header>
</template>

<script setup>
import BaseModal from './BaseModal.vue'
import { ref } from 'vue'

const modalActive = ref(null)

const toggleModal = () => {
  modalActive.value = !modalActive.value
}
</script>
