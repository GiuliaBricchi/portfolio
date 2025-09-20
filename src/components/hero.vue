<template>
  <section class="relative w-full h-[calc(100vh-80px)] flex items-center justify-center overflow-hidden pt-20">
    <!-- Sfondo -->
    <div class="absolute inset-0 bg-center bg-cover z-0" :style="{ backgroundImage: `url(${bg})` }"></div>

    <!-- Titolo sopra -->
    <h1
      class="relative z-10 font-mono text-4xl text-[#475c69] whitespace-nowrap overflow-hidden border-r-4 border-[#475c69] w-0 animate-typing"
    >
      Nice to see you
    </h1>
  </section>
</template>

<script setup>
import bg from '../assets/sfondo.png'
</script>

<style scoped>
@keyframes typing {
  from { width: 0; }
  to { width: 16ch; }
}

@keyframes blink {
  50% { border-color: transparent; }
}

.animate-typing {
  animation: typing 3.5s steps(15, end) forwards, blink 0.7s step-end infinite 3.5s;
}
</style>
