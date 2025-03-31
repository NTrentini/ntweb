<template>
    <div class="navbar sticky top-0 z-50 h-12" :class="{ 'is-scrolled': isScrolled }">
      <div class="absolute top-0 left-0 w-full h-0 transition-all duration-300 z-[-1]" :class="{ 'h-full': isScrolled }"></div>
      <div class="container mx-auto px-4 py-4 flex items-center justify-between">
        <div class="logo">
          <img src="../assets/logo.svg" alt="Logo" class="h-12">
        </div>
        <div class="hidden md:flex space-x-4 items-center">
          <a href="#" class="text-gray-700 hover:underline">Serviços</a>
          <a href="#" class="text-gray-700 hover:underline">Portfolio</a>
          <a href="#" class="text-gray-700 hover:underline">Sobre</a>
          <button class="bg-orange-500 text-black px-4 py-2 rounded">Contato</button>
        </div>
        <div class="md hidden relative">
          <button @click="toggleMenu" class="text-gray-700 focus:outline-none">
            <svg class="h-6 w-6" stroke="currentColor" fill="none" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
            </svg>
          </button>
          <div v-if="isMenuOpen" class="absolute right-0 mt-2 w-48 bg-white shadow-md p-4">
            <a href="#" class="block text-gray-700 hover:underline mb-2">Link 1</a>
            <a href="#" class="block text-gray-700 hover:underline mb-2">Link 2</a>
            <a href="#" class="block text-gray-700 hover:underline mb-2">Link 3</a>
            <button class="bg-blue-500 text-white px-4 py-2 rounded w-full">Button</button>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import { ref, onMounted, onBeforeUnmount } from 'vue'
  
  export default {
    setup() {
      const isScrolled = ref(false)
      const isMenuOpen = ref(false)
  
      const handleScroll = () => {
        isScrolled.value = window.scrollY > 0
      }
  
      onMounted(() => {
        window.addEventListener('scroll', handleScroll)
      })
  
      onBeforeUnmount(() => {
        window.removeEventListener('scroll', handleScroll)
      })
  
      const toggleMenu = () => {
        isMenuOpen.value = !isMenuOpen.value
      }
  
      return {
        isScrolled,
        isMenuOpen,
        toggleMenu
      }
    }
  }
  </script>