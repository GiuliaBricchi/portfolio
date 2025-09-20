<template>
  <section id="projects">
    <!-- ---------- SCHERMATA INTRO ---------- -->
    <div class="project-intro">
      <h1>Projects</h1>
    </div>

    <!-- ---------- PROGETTO 1 ---------- -->
    <div class="project-detail project-blue">
      <div class="project-info">
        <h2>Logo Design</h2>
        <p class="year">2025</p>
        <p class="mini-description">
          Creating a unique visual identity through a memorable and recognizable logo.
          For Antonio, the project involved analyzing the brand, selecting a coherent
          color palette, and choosing suitable typography, with the goal of immediately
          conveying the company’s values and personality.
        </p>
      </div>
      <div class="project-images">
        <div v-for="(img, index) in logoImages" :key="`logo-${index}`" class="image-card">
          <img :src="img" alt="Logo Project Image" />
        </div>
      </div>
    </div>

    <!-- ---------- PROGETTO 2 ---------- -->
    <div class="project-detail project-default">
      <div class="project-info">
        <h2>Rebranding</h2>
        <p class="year">2024</p>
        <p class="mini-description">
          Complete revamp of the company’s visual identity: from the logo to the color palette,
          and including the creation of new coordinated graphic elements. The goal was to convey
          modernity and visual consistency, strengthening the brand identity and enhancing its
          recognition in the market.
        </p>
      </div>
      <div class="project-images">
        <div v-for="(img, index) in rebrandingImages" :key="`re-${index}`" class="image-card">
          <img :src="img" alt="Rebranding Project Image" />
        </div>
      </div>
    </div>

    <!-- ---------- PROGETTO 3 ---------- -->
    <div class="project-detail project-blue">
      <div class="project-info">
        <h2>App Design</h2>
        <p class="year">2024</p>
        <p class="mini-description">
          Design of intuitive and modern interfaces for a mobile app, focusing on user
          experience and ensuring simple, smooth navigation.
        </p>
      </div>
      <div class="project-images">
        <div v-for="(img, index) in appDesignImages" :key="`app-${index}`" class="image-card">
          <img :src="img" alt="App Design Project Image" />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
/* --- PROGETTO 1: Logo (6 immagini) --- */
import Logo1 from '../assets/projects/logo/l1.png'
import Logo2 from '../assets/projects/logo/l2.png'
import Logo3 from '../assets/projects/logo/l3.png'
import Logo4 from '../assets/projects/logo/l4.png'
import Logo5 from '../assets/projects/logo/l5.JPG'
import Logo6 from '../assets/projects/logo/l6.png'
const logoImages = [Logo1, Logo2, Logo3, Logo4, Logo5, Logo6]

/* --- PROGETTO 2: Rebranding (6 immagini) --- */
import Re1 from '../assets/projects/rebranding/re1.JPG'
import Re2 from '../assets/projects/rebranding/re2.JPG'
import Re3 from '../assets/projects/rebranding/re3.JPG'
import Re4 from '../assets/projects/rebranding/re4.JPG'
import Re5 from '../assets/projects/rebranding/re5.JPG'
import Re6 from '../assets/projects/rebranding/re6.JPG'
const rebrandingImages = [Re1, Re2, Re3, Re4, Re5, Re6]

/* --- PROGETTO 3: App Design (6 immagini) --- */
import App1 from '../assets/projects/app/app1.png'
import App2 from '../assets/projects/app/app2.png'
import App3 from '../assets/projects/app/app3.png'
import App4 from '../assets/projects/app/app4.png'
import App5 from '../assets/projects/app/app5.png'
import App6 from '../assets/projects/app/app6.png'
const appDesignImages = [App1, App2, App3, App4, App5, App6]
</script>

<style scoped>
/* ---------- FORZA NESSUNO SCROLL ORIZZONTALE ---------- */
body, #projects {
  overflow-x: hidden;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* ---------- SCHERMATA INTRO ---------- */
.project-intro {
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: url('../assets/projects/arrow.png') center/cover no-repeat;
}

.project-intro h1 {
  font-size: 5rem;
  font-weight: bold;
  color: #475c69;
  text-transform: uppercase;
  letter-spacing: 5px;
  margin: 0;
  background: rgba(255, 255, 255, 0.6);
  padding: 1rem 2rem;
  border-radius: 12px;
}

/* ---------- SEZIONE PROGETTI FULL SCREEN ---------- */
.project-detail {
  display: grid;
  grid-template-columns: 1fr 2fr;
  width: 100vw;
  max-width: 1400px;
  margin: 0 auto 4rem auto;
  padding: 2rem 1rem;
  gap: 2rem;
  align-items: flex-start;
  border-radius: 12px;
  box-sizing: border-box;
}

/* ---------- Background alternati ---------- */
.project-default {
  background: #f8f8f8;
  color: #333;
}

.project-blue {
  background: #475c69;
  color: #f8f8f8;
}

/* Colonna sinistra */
.project-info {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  padding: 4rem 2rem 0 2rem;
}

.project-info h2 {
  font-size: 3rem;
  margin: 0 0 1rem 0;
}

.project-info .year {
  font-size: 1.2rem;
  font-weight: bold;
  margin: 0.5rem 0 1rem 0;
}

.project-info .mini-description {
  font-size: 1rem;
  line-height: 1.6;
  margin-top: 0;
}

/* Colonna destra: griglia immagini */
.project-images {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: 1fr;
  gap: 1rem;
  width: 100%;
  max-width: 100%;
}

.image-card {
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 6px 18px rgba(0, 0, 0, 0.08);
  background: #eee;
}

.image-card img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  max-width: 100%;
}

/* ---------- Responsive ---------- */
@media (max-width: 1024px) {
  .project-detail {
    grid-template-columns: 1fr;
    height: auto;
  }
  .project-images {
    grid-template-columns: 2fr 1fr;
    grid-auto-rows: auto;
    justify-self: center;
  }
}

@media (max-width: 768px) {
  .project-detail {
    padding: 1.5rem;
    gap: 1.5rem;
  }
  .project-info {
    padding: 2rem 1rem 0 1rem;
  }
  .project-images {
    grid-template-columns: 1fr;
    grid-auto-rows: auto;
    width: 100%;
  }
}
</style>