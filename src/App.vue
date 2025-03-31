
<script >
import { ref, onMounted, onBeforeUnmount } from 'vue'
import './styles.css';
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
<template>
  <div class="navbar sticky top-0 z-50 h-12" :class="{ 'is-scrolled': isScrolled }">
    <div class="absolute top-0 left-0 w-full h-0 transition-all duration-300 z-[-1]" :class="{ 'h-full': isScrolled }"></div>
      <div class="container mx-auto px-2 py-5 flex items-center justify-between">
          <div class="logo">
              <img src="./assets/logo.svg" alt="Logo" class="h-15">
          </div>
      </div>
    </div>
  <div class="min-h-screen absolute top-0 w-full align-center flex flex-col justify-center items-center bg-[url(../assets/bg-banner-nt-web2.jpg)] bg-cover bg-no-repeat bg-center">
      <img src="./assets/n-logo-dist.png" alt="NT Web" class="h-80 mb-4">
      <h1 class="text-4xl text-white font-rubikglitch uppercase" >
          Atualização em andamento...
      </h1>
  <p class="p-4 text-white max-w-160 align-center text-center">Olá, nosso site está em manutenção e não pode ser acessado no momento. <br/>Utilize os links abaixo para entrar em contato ou volte mais tarde</p>
  <div class="flex flex-row items-center justify-center mt-4 px-4"> 
    <a href="https://wa.me/5547999114558" target="_blank" class="text-ntorange opacity-90 hover:opacity-100 transition-opacity duration-300 mx-3"><img class="w-8 h-8" fill="currentColor" src="./assets/social/whatsapp.svg" /></a>
    <a href="mailto:ntrentini@me.com" target="_blank" class="text-ntorange opacity-90 hover:opacity-100 transition-opacity duration-300 mx-3"><img class="w-8 h-8" fill="currentColor" src="./assets/social/email.svg" /></a>
    <a href="https://www.instagram.com/ntweb.design/" target="_blank" class="text-ntorange opacity-90 hover:opacity-100 transition-opacity duration-300 mx-3"><img class="w-8 h-8" fill="currentColor" src="./assets/social/instagram.svg" /></a>
    <a href="https://www.linkedin.com/in/ntrentini/" target="_blank" class="text-ntorange opacity-90 hover:opacity-100 transition-opacity duration-300 mx-3"><img class="w-8 h-8" fill="currentColor" src="./assets/social/linkedin.svg" /></a>
    <a href="https://www.behance.net/ntrentini" target="_blank" class="text-ntorange opacity-90 hover:opacity-100 transition-opacity duration-300 mx-3"><img class="w-8 h-8" fill="currentColor" src="./assets/social/behance.svg" /></a> 
  </div>
</div>
</template>

