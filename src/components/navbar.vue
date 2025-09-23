<template>
  <div>
    <!-- Navbar -->
    <nav
      class="fixed top-0 left-0 w-full h-20 flex items-center justify-between px-8 bg-white z-50 transition-transform duration-300"
      :class="{ '-translate-y-full': isHidden }"
    >

      <div>
        <img :src="logo" alt="Logo" class="h-20" />
      </div>

      <div class="hidden md:flex justify-center items-center bg-gray-200/50 px-6 py-2 rounded-full">
        <ul class="flex gap-6 font-bold text-gray-700">
          <li><a href="#about" class="hover:underline">about</a></li>
          <li><a href="#skills" class="hover:underline">skills</a></li>
          <li><a href="#projects" class="hover:underline">projects</a></li>
          <li><a href="#contact" class="hover:underline">contact</a></li>
        </ul>
      </div>

      <div class="flex items-center gap-2 flex-shrink-0">
        <button
          class="hidden md:flex items-center gap-2 px-4 py-2 rounded-full font-bold bg-gray-200/50 text-gray-700 hover:text-white hover:bg-gray-700 transition"
          @click="openModal"
        >
          start project <span class="transition-transform">🡭</span>
        </button>

        <button
          class="md:hidden w-12 h-12 rounded-full flex items-center justify-center bg-gray-200/50 text-gray-700 hover:bg-gray-700 hover:text-white transition"
          @click="openModal"
          aria-label="start project"
        >🡭</button>

        <button
          class="md:hidden text-2xl text-gray-700"
          @click="toggleMenu"
        >☰</button>
      </div>
    </nav>

    <!-- Mobile menu -->
    <div v-if="isOpen" class="fixed inset-0 bg-white/80 backdrop-blur flex flex-col items-center justify-center gap-8 z-40">
      <button
        class="absolute top-5 right-5 text-2xl text-gray-700"
        @click="closeMenu"
        aria-label="Close menu"
      >✕</button>
      <ul class="flex flex-col gap-8 text-center text-2xl font-bold text-gray-700">
        <li><a href="#about" @click="closeMenu">about</a></li>
        <li><a href="#skills" @click="closeMenu">skills</a></li>
        <li><a href="#projects" @click="closeMenu">projects</a></li>
        <li><a href="#contact" @click="closeMenu">contact</a></li>
      </ul>
    </div>

    <!-- Start Project -->
    <div v-if="isModalOpen" class="fixed inset-0 bg-black/70 flex items-center justify-center z-50 p-4">
      <div class="relative bg-white w-full max-w-lg rounded-xl shadow-lg p-6 overflow-y-auto max-h-[90vh]">
        <button
          class="absolute top-4 right-4 text-xl text-gray-700"
          @click="closeModal"
        >✕</button>
        <h2 class="text-xl font-semibold text-center text-gray-700 mb-4">Start a Project</h2>
        <form class="flex flex-col gap-4">
          <input type="text" placeholder="Name" required class="p-3 border rounded-lg" />
          <input type="text" placeholder="Surname" required class="p-3 border rounded-lg" />
          <input type="tel" placeholder="Phone number" required class="p-3 border rounded-lg" />
          <input type="email" placeholder="Email" required class="p-3 border rounded-lg" />
          <input type="text" placeholder="Project type" required class="p-3 border rounded-lg" />
          <textarea placeholder="Message content" rows="5" required class="p-3 border rounded-lg"></textarea>
          <button
            type="submit"
            class="bg-gray-700 text-white py-3 rounded-lg font-bold hover:bg-gray-900 transition"
          >Send</button>
        </form>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import logo from '../assets/bricchinilogo.png'

const isHidden = ref(false)
const isOpen = ref(false)
const isModalOpen = ref(false)
let lastScrollY = 0

const toggleMenu = () => { isOpen.value = !isOpen.value }
const closeMenu = () => { isOpen.value = false }

const openModal = () => { isModalOpen.value = true }
const closeModal = () => { isModalOpen.value = false }

const handleScroll = () => {
  if (window.scrollY > lastScrollY && window.scrollY > 80) {
    isHidden.value = true
  } else {
    isHidden.value = false
  }
  lastScrollY = window.scrollY
}

onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>
