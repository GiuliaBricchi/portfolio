<template>
  <section id="about" class="about mt-32 min-h-screen py-32" ref="aboutSection">
    <div class="about-photo">
      <!-- Prima polaroid -->
      <div class="polaroid animate">
        <div class="img-wrapper">
          <img src="../assets/about/me.jpg" alt="Foto" />
        </div>
      </div>

      <!-- Seconda polaroid -->
      <div v-if="showSecond" class="polaroid overlay overlay-second">
        <div class="img-wrapper">
          <img src="../assets/about/me2.JPEG" alt="Seconda foto" />
        </div>
      </div>

      <!-- Terza polaroid -->
      <div v-if="showThird" class="polaroid overlay overlay-third">
        <div class="img-wrapper">
          <img src="../assets/about/me3.JPEG" alt="Terza foto" />
        </div>
      </div>
    </div>

    <div class="about-text">
      <h2>About Me</h2>

      <p v-if="!showSecond && !showThird">
        ✨ Hi! I’m Giulia Bricchi, I’m 26 years old and I live in Brescia.
        In the creative world, you’ll find me as Bricchini. I love observing,
        experimenting, and turning ideas into images that tell stories.
        Curious, a little ironic, and always ready to discover new inspirations.
      </p>

      <p v-else-if="showSecond && !showThird">
        🎓 I studied graphic design since high school, attending the Golgi institute with a focus on Graphics.
        I began my university journey by graduating in Graphic Design at Accademia di Belle Arti Santa Giulia in Brescia, where I honed my skills in visual design and communication.
        I then continued my path with a master's degree in Digital Design & Communication at Laba.
      </p>

      <p v-else-if="showThird">
        📸 In addition to design, I love traveling and discovering new places, bringing with me my passion for photography, capturing moments, lights, and details that tell stories.
        I believe that an image can communicate more than a thousand words when seen with the right eye.
        <br /><br />
        What does my future hold? Let’s find out together! 🚀
      </p>

      <!-- Bottoni dinamici -->
      <button v-if="!showSecond" class="about-btn" @click="showSecond = true">
        check it out!
      </button>
      <button v-else-if="!showThird" class="about-btn" @click="showThird = true">
        more and more
      </button>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from "vue"

const aboutSection = ref(null)
const isVisible = ref(false)
const showSecond = ref(false)
const showThird = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver(
    entries => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          isVisible.value = true
          observer.unobserve(entry.target)
        }
      })
    },
    { threshold: 0.3 }
  )

  if (aboutSection.value) observer.observe(aboutSection.value)
})
</script>

<style scoped>
.about {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 4rem 2rem;
  gap: 2rem;
  min-height: 100vh;
  position: relative;
}

.about-photo {
  position: relative;
  width: 350px;
  height: 450px;
}

.polaroid {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  padding: 10px 10px 80px 10px;
  background: #fff;
  border-radius: 15px;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
  overflow: hidden;
  transition: transform 1s ease-out, opacity 1s ease-out;
}

.img-wrapper {
  width: 100%;
  padding-top: 100%;
  position: relative;
  overflow: hidden;
  border-radius: 10px;
}

.img-wrapper img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* Animazioni */
.polaroid.animate {
  transform: translateX(-100px) rotate(-10deg);
  opacity: 1;
}

.polaroid.overlay-second {
  transform: translate(-60px, 30px) rotate(18deg);
  opacity: 0;
  animation: slideIn 1s forwards;
  z-index: 2;
}

.polaroid.overlay-third {
  transform: translate(-30px, -40px) rotate(-15deg);
  opacity: 0;
  animation: slideInThird 1s forwards;
  z-index: 3;
}

@keyframes slideIn {
  from {
    transform: translateY(-50px) rotate(18deg);
    opacity: 0;
  }
  to {
    transform: translate(-60px, 30px) rotate(18deg);
    opacity: 1;
  }
}

@keyframes slideInThird {
  from {
    transform: translateY(-50px) rotate(-15deg);
    opacity: 0;
  }
  to {
    transform: translate(-30px, -40px) rotate(-15deg);
    opacity: 1;
  }
}


.about-text {
  max-width: 500px;
}
.about-text h2 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  color: #475c69;
}
.about-text p {
  font-size: 1.1rem;
  line-height: 1.5;
  color: #333;
}

.about-btn {
  margin-top: 1.5rem;
  padding: 10px 20px;
  border: none;
  background-color: #475c69;
  color: white;
  font-size: 1rem;
  font-weight: 500;
  border-radius: 8px;
  cursor: pointer;
  transition: background 0.3s ease, transform 0.2s ease;
}
.about-btn:hover {
  background-color: #2f3f48;
  transform: translateY(-2px);
}


@media (max-width: 768px) {
  .about {
    flex-direction: column;
    align-items: center;
    text-align: center;
  }
  .about-photo {
    margin-bottom: 2rem;
  }
}
</style>
