<template>
  <section id="skills" class="skills-section py-32">
    <h2 class="text-3xl font-bold mb-4">Skills</h2>
    <p class="mb-8 text-lg">Tools and software I use:</p>

    <div class="skills-icons flex flex-wrap justify-center gap-8">
      <div class="skill flex flex-col items-center gap-2" v-for="(skill, index) in skills" :key="index">
        <img :src="skill.icon" :alt="skill.name" class="skill-icon w-16 h-16 object-contain" />
        <span>{{ skill.name }}</span>
      </div>
    </div>
  </section>
</template>

<script setup>
import illustrator from '../assets/skills/illustrator.png'
import indesign from '../assets/skills/indesign.png'
import photoshop from '../assets/skills/photoshop.png'
import aftereffects from '../assets/skills/aftereffects.png'
import figma from '../assets/skills/figma.png'
import protopie from '../assets/skills/protopie.png'

const skills = [
  { name: 'Illustrator', icon: illustrator },
  { name: 'InDesign', icon: indesign },
  { name: 'Photoshop', icon: photoshop },
  { name: 'After Effects', icon: aftereffects },
  { name: 'Figma', icon: figma },
  { name: 'ProtoPie', icon: protopie }
]
</script>

<style scoped>
.skills-section {
  padding: 6rem 2rem;
  text-align: center;
  background-color: #475c69;
  color: #ffffff;
}

.skills-section h2 {
  font-size: 2rem;
  margin-bottom: 1rem;
}

.skills-section p {
  font-size: 1rem;
  margin-bottom: 2rem;
}

.skills-icons {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 2rem;
}

.skill {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
}

.skill-icon {
  width: 60px;
  height: 60px;
  object-fit: contain;
}

/* Responsive */
@media (max-width: 768px) {
  .skills-section {
    padding: 4rem 1rem;
  }
  .skills-icons {
    gap: 1.5rem;
  }
  .skill-icon {
    width: 50px;
    height: 50px;
  }
}
</style>