<template>
  <div class="app" :class="{ 'cursor--hover': cursorHover }">
    <!-- Custom cursor -->
    <div class="cursor" :style="cursorStyle"></div>
    <div class="cursor cursor--ring" :style="ringStyle"></div>

    <!-- Noise texture -->
    <div class="noise" aria-hidden="true"></div>

    <AppHeader />
    <main>
      <HeroSection />
      <MarqueeSection />
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
import { ref, onMounted, onUnmounted } from 'vue'
import AppHeader from './components/AppHeader.vue'
import HeroSection from './components/HeroSection.vue'
import MarqueeSection from './components/MarqueeSection.vue'
import AboutSection from './components/AboutSection.vue'
import ClassesSection from './components/ClassesSection.vue'
import FeaturesSection from './components/FeaturesSection.vue'
import ScheduleSection from './components/ScheduleSection.vue'
import ContactSection from './components/ContactSection.vue'
import AppFooter from './components/AppFooter.vue'

const mx = ref(0), my = ref(0)
const rx = ref(0), ry = ref(0)
const cursorHover = ref(false)

const cursorStyle = ref({})
const ringStyle = ref({})

let rafId = null
let targetX = 0, targetY = 0
let ringX = 0, ringY = 0

function onMove(e) {
  targetX = e.clientX
  targetY = e.clientY
}

function tick() {
  mx.value += (targetX - mx.value) * 0.85
  my.value += (targetY - my.value) * 0.85
  ringX += (targetX - ringX) * 0.12
  ringY += (targetY - ringY) * 0.12

  cursorStyle.value = { transform: `translate(calc(${mx.value}px - 50%), calc(${my.value}px - 50%))` }
  ringStyle.value = { transform: `translate(calc(${ringX}px - 50%), calc(${ringY}px - 50%))` }
  rafId = requestAnimationFrame(tick)
}

function onHoverIn() { cursorHover.value = true }
function onHoverOut() { cursorHover.value = false }

// Scroll reveal
function initReveal() {
  const els = document.querySelectorAll('.reveal')
  const io = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('is-visible')
        io.unobserve(e.target)
      }
    })
  }, { threshold: 0.12 })
  els.forEach(el => io.observe(el))
}

onMounted(() => {
  window.addEventListener('mousemove', onMove)
  rafId = requestAnimationFrame(tick)

  document.querySelectorAll('a, button, [data-hover]').forEach(el => {
    el.addEventListener('mouseenter', onHoverIn)
    el.addEventListener('mouseleave', onHoverOut)
  })

  setTimeout(initReveal, 100)
})

onUnmounted(() => {
  window.removeEventListener('mousemove', onMove)
  cancelAnimationFrame(rafId)
})
</script>

<style>
.app { min-height: 100vh; background: var(--black); }
</style>
