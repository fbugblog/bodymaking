<template>
  <div class="app">
    <AppHeader />
    <main>
      <HeroSection />
      <AboutSection />
      <ClassesSection />
      <FeaturesSection />
      <ScheduleSection />
      <ContactSection />
    </main>
    <AppFooter />
  </div>
</template>

<script setup>
import AppHeader from './components/AppHeader.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import ClassesSection from './components/ClassesSection.vue'
import FeaturesSection from './components/FeaturesSection.vue'
import ScheduleSection from './components/ScheduleSection.vue'
import ContactSection from './components/ContactSection.vue'
import AppFooter from './components/AppFooter.vue'
</script>

<style>
.app {
  min-height: 100vh;
}
</style>
