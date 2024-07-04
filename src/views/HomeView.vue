<template>
  <div class="container-fluid">
    <section class="row" id="landing">
      <LandingSection />
    </section>
    <section class="row" id="about">
      <AboutSection />
    </section>
    <section class="row" id="resume">
      <ResumeSection />
    </section>
    <section class="row" id="skills">
      <SkillsSection />
    </section>
    <section class="row" id="testimonials">
      <TestimonialsSection />
    </section>
    <section class="row" id="projects">
      <ProjectsSection />
    </section>
    <section class="row" id="reachMe">
      <ReachMeSection />
    </section>
  </div>
</template>

<script>
import LandingSection from '@/components/LandingSection.vue'
import AboutSection from '@/components/AboutSection.vue'
import ResumeSection from '@/components/ResumeSection.vue'
import SkillsSection from '@/components/SkillsSection.vue'
import TestimonialsSection from '@/components/TestimonialsSection.vue'
import ProjectsSection from '@/components/ProjectsSection.vue'
import ReachMeSection from '@/components/ReachMeSection.vue'
export default {
  name: 'HomeView',
  components: {
    LandingSection, AboutSection, ResumeSection, SkillsSection,TestimonialsSection, ProjectsSection, ReachMeSection
  }
}
</script>

<style scoped>

</style>
