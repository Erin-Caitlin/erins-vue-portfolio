<template>
  <div class="container">
    <section class="row" id="landing">
      <LandingSection />
    </section>
    <section class="row" id="about">
      <AboutSection />
    </section>
    <section class="row" id="resume">
      <ResumeSection />
    </section>
    <section class="row" id="testimonials">

    </section>
    <section class="row" id="projects">

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
import ReachMeSection from '@/components/ReachMeSection.vue'
export default {
  name: 'HomeView',
  components: {
    LandingSection, AboutSection, ResumeSection, ReachMeSection
  }
}
</script>
