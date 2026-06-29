<template>
  <div class="app">
    <!-- Custom cursor (desktop only) -->
    <template v-if="!isTouch">
      <div class="cursor" :class="{ 'cursor--big': cursorHover }" :style="cursorStyle"></div>
      <div class="cursor cursor--ring" :class="{ 'cursor--ring-big': cursorHover }" :style="ringStyle"></div>
    </template>

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

const isTouch = ref(false)
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
  const mx = (targetX - parseFloat(cursorStyle.value.transform?.match(/-?\d+\.?\d*/)?.[0] || 0)) * 0.85
  const my = (targetY - parseFloat(cursorStyle.value.transform?.match(/-?\d+\.?\d*/g)?.[1] || 0)) * 0.85

  // Simple lerp tracking
  if (!tick.cx) tick.cx = 0
  if (!tick.cy) tick.cy = 0
  tick.cx += (targetX - tick.cx) * 0.85
  tick.cy += (targetY - tick.cy) * 0.85
  ringX += (targetX - ringX) * 0.12
  ringY += (targetY - ringY) * 0.12

  cursorStyle.value = { transform: `translate(calc(${tick.cx}px - 50%), calc(${tick.cy}px - 50%))` }
  ringStyle.value = { transform: `translate(calc(${ringX}px - 50%), calc(${ringY}px - 50%))` }
  rafId = requestAnimationFrame(tick)
}

function initCursor() {
  window.addEventListener('mousemove', onMove)
  rafId = requestAnimationFrame(tick)
  document.querySelectorAll('a, button, [data-hover]').forEach(el => {
    el.addEventListener('mouseenter', () => { cursorHover.value = true })
    el.addEventListener('mouseleave', () => { cursorHover.value = false })
  })
}

function initReveal() {
  const els = document.querySelectorAll('.reveal')
  if (!els.length) return
  const io = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('is-visible')
        io.unobserve(e.target)
      }
    })
  }, { threshold: 0.08, rootMargin: '0px 0px -40px 0px' })
  els.forEach(el => io.observe(el))
}

onMounted(() => {
  // Detect touch device
  isTouch.value = window.matchMedia('(pointer: coarse)').matches
    || 'ontouchstart' in window

  if (!isTouch.value) {
    initCursor()
  }

  setTimeout(initReveal, 150)
})

onUnmounted(() => {
  if (!isTouch.value) {
    window.removeEventListener('mousemove', onMove)
    cancelAnimationFrame(rafId)
  }
})
</script>

<style>
.app { min-height: 100vh; min-height: 100dvh; background: var(--black); }

/* Custom cursor — desktop only */
.cursor {
  position: fixed;
  top: 0; left: 0;
  width: 10px; height: 10px;
  background: var(--pink);
  border-radius: 50%;
  pointer-events: none;
  z-index: 9999;
  transform: translate(-50%, -50%);
  transition: width .3s var(--ease-expo), height .3s var(--ease-expo);
  mix-blend-mode: difference;
}
.cursor--ring {
  width: 36px; height: 36px;
  background: transparent;
  border: 1px solid rgba(233, 30, 140, 0.5);
  transition: width .5s var(--ease-expo), height .5s var(--ease-expo), border-color .3s;
}
.cursor--big { width: 48px; height: 48px; }
.cursor--ring-big { width: 56px; height: 56px; border-color: var(--pink); }
</style>
