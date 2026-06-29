<template>
  <!-- Wrapper div needed for two sibling elements -->
  <div class="header-root">
    <header class="header" :class="{ scrolled: isScrolled }">
      <div class="container header__inner">
        <a href="#top" class="logo">
          <svg class="logo__mark" viewBox="0 0 40 40" fill="none">
            <circle cx="20" cy="20" r="19" stroke="url(#lg)" stroke-width="1"/>
            <path d="M20 8 C20 8 28 14 28 20 C28 26 20 32 20 32 C20 32 12 26 12 20 C12 14 20 8 20 8Z" stroke="url(#lg)" stroke-width="1" fill="none"/>
            <defs>
              <linearGradient id="lg" x1="0" y1="0" x2="40" y2="40">
                <stop offset="0%" stop-color="#FF6BC1"/>
                <stop offset="100%" stop-color="#C9A96E"/>
              </linearGradient>
            </defs>
          </svg>
          <span class="logo__text">
            <span class="logo__en">Studio Grace</span>
            <span class="logo__ja">ボディメイキング・新体操</span>
          </span>
        </a>

        <!-- Desktop navigation -->
        <nav class="desktop-nav" aria-label="メインナビゲーション">
          <ul class="desktop-nav__list">
            <li v-for="(item, i) in nav" :key="item.href">
              <a :href="item.href" class="desktop-nav__link">
                <span class="desktop-nav__num">{{ String(i+1).padStart(2,'0') }}</span>
                <span>{{ item.label }}</span>
              </a>
            </li>
          </ul>
          <a href="#contact" class="btn-glow desktop-nav__cta">無料体験</a>
        </nav>

        <!-- Hamburger — always on top -->
        <button
          class="hamburger"
          :class="{ active: menuOpen }"
          @click="toggleMenu"
          :aria-expanded="menuOpen"
          aria-label="メニューを開く"
        >
          <span></span>
          <span></span>
          <span></span>
        </button>
      </div>
    </header>

    <!-- Mobile full-screen overlay — SIBLING of header, not child -->
    <div
      class="mobile-menu"
      :class="{ 'mobile-menu--open': menuOpen }"
      aria-modal="true"
      role="dialog"
      aria-label="ナビゲーションメニュー"
    >
      <nav class="mobile-menu__nav">
        <ul class="mobile-menu__list">
          <li v-for="(item, i) in nav" :key="item.href">
            <a :href="item.href" class="mobile-menu__link" @click="closeMenu">
              <span class="mobile-menu__num">{{ String(i+1).padStart(2,'0') }}</span>
              <span>{{ item.label }}</span>
            </a>
          </li>
        </ul>
        <a href="#contact" class="btn-glow mobile-menu__cta" @click="closeMenu">無料体験を申し込む</a>
      </nav>

      <!-- Decorative bg -->
      <div class="mobile-menu__deco" aria-hidden="true"></div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const menuOpen = ref(false)

const nav = [
  { href: '#about',    label: 'About' },
  { href: '#classes',  label: 'Classes' },
  { href: '#features', label: 'Why Us' },
  { href: '#schedule', label: 'Schedule' },
  { href: '#contact',  label: 'Contact' },
]

function toggleMenu() {
  menuOpen.value = !menuOpen.value
  // Prevent body scroll when menu is open
  document.body.style.overflow = menuOpen.value ? 'hidden' : ''
}

function closeMenu() {
  menuOpen.value = false
  document.body.style.overflow = ''
}

function onScroll() {
  isScrolled.value = window.scrollY > 60
}

onMounted(() => window.addEventListener('scroll', onScroll, { passive: true }))
onUnmounted(() => {
  window.removeEventListener('scroll', onScroll)
  document.body.style.overflow = ''
})
</script>

<style scoped>
/* ── Header ─────────────────────────────────────────────── */
.header {
  position: fixed;
  top: 0; left: 0; width: 100%;
  z-index: 300;
  padding: 22px 0;
  transition: padding .4s var(--ease-expo), background .4s, box-shadow .4s;
}

.header.scrolled {
  padding: 12px 0;
  background: rgba(6, 4, 8, 0.88);
  backdrop-filter: blur(20px) saturate(180%);
  -webkit-backdrop-filter: blur(20px) saturate(180%);
  box-shadow: 0 1px 0 rgba(233, 30, 140, 0.06);
}

.header__inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 24px;
}

/* ── Logo ─────────────────────────────────────────────── */
.logo {
  display: flex;
  align-items: center;
  gap: 12px;
  flex-shrink: 0;
  z-index: 1;
}
.logo__mark {
  width: 34px; height: 34px;
  flex-shrink: 0;
  animation: rotateMark 14s linear infinite;
}
@keyframes rotateMark {
  to { transform: rotate(360deg); }
}
.logo__text {
  display: flex;
  flex-direction: column;
  line-height: 1.1;
}
.logo__en {
  font-family: var(--font-serif);
  font-size: 18px;
  font-weight: 400;
  letter-spacing: 0.06em;
  background: linear-gradient(90deg, #fff 0%, rgba(255,255,255,.75) 100%);
  -webkit-background-clip: text; background-clip: text;
  -webkit-text-fill-color: transparent;
}
.logo__ja {
  font-size: 9px;
  letter-spacing: 0.1em;
  color: var(--gray);
}

/* ── Desktop Nav ─────────────────────────────────────── */
.desktop-nav {
  display: flex;
  align-items: center;
  gap: 36px;
}
.desktop-nav__list {
  display: flex;
  align-items: center;
  gap: 28px;
  list-style: none;
}
.desktop-nav__link {
  display: flex;
  align-items: center;
  gap: 5px;
  font-size: 12px;
  letter-spacing: 0.1em;
  color: rgba(255,255,255,0.5);
  transition: color .3s;
  position: relative;
  padding-bottom: 2px;
}
.desktop-nav__link::after {
  content: '';
  position: absolute;
  bottom: 0; left: 0;
  width: 0; height: 1px;
  background: linear-gradient(90deg, var(--pink), var(--gold));
  transition: width .4s var(--ease-expo);
}
.desktop-nav__link:hover { color: white; }
.desktop-nav__link:hover::after { width: 100%; }
.desktop-nav__num {
  font-family: var(--font-serif);
  font-size: 9px;
  font-weight: 300;
  color: var(--pink-light);
  opacity: 0.45;
}
.desktop-nav__cta { font-size: 12px; padding: 10px 26px; }

/* ── Hamburger ──────────────────────────────────────── */
.hamburger {
  display: none;
  flex-direction: column;
  gap: 6px;
  padding: 8px;
  position: relative;
  z-index: 400; /* always above the mobile overlay */
}
.hamburger span {
  display: block;
  width: 24px; height: 1.5px;
  background: white;
  transform-origin: center;
  transition: all .35s var(--ease-expo);
}
.hamburger.active span:nth-child(1) { transform: translateY(7.5px) rotate(45deg); }
.hamburger.active span:nth-child(2) { opacity: 0; transform: scaleX(0); }
.hamburger.active span:nth-child(3) { transform: translateY(-7.5px) rotate(-45deg); }

/* ── Mobile Menu Overlay ────────────────────────────── */
.mobile-menu {
  /* OUTSIDE the header — its own stacking context */
  position: fixed;
  inset: 0;
  z-index: 250; /* below header (300) but above everything else */
  background: var(--deep);
  display: flex;
  align-items: center;
  justify-content: center;
  pointer-events: none;   /* ← closed: block NO touches */
  opacity: 0;
  transform: translateX(100%);
  transition: transform .5s var(--ease-expo), opacity .4s;
  overflow: hidden;
}
.mobile-menu--open {
  pointer-events: auto;   /* ← open: accept touches */
  opacity: 1;
  transform: translateX(0);
}

.mobile-menu__nav {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 48px;
  position: relative;
  z-index: 1;
  padding: 80px 40px 40px; /* top padding clears header */
}
.mobile-menu__list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 28px;
  text-align: center;
}
.mobile-menu__link {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  font-size: 24px;
  letter-spacing: 0.06em;
  color: rgba(255,255,255,0.65);
  transition: color .3s;
  position: relative;
}
.mobile-menu__link::after {
  content: '';
  position: absolute;
  bottom: -4px; left: 50%;
  transform: translateX(-50%);
  width: 0; height: 1px;
  background: linear-gradient(90deg, var(--pink), var(--gold));
  transition: width .4s var(--ease-expo);
}
.mobile-menu__link:hover,
.mobile-menu__link:active { color: white; }
.mobile-menu__link:hover::after { width: 80%; }
.mobile-menu__num {
  font-family: var(--font-serif);
  font-size: 12px;
  color: var(--pink-light);
  opacity: 0.4;
}
.mobile-menu__cta { font-size: 15px; padding: 16px 48px; }

.mobile-menu__deco {
  position: absolute;
  inset: 0;
  background:
    radial-gradient(circle at 80% 20%, rgba(233,30,140,0.08) 0%, transparent 50%),
    radial-gradient(circle at 20% 80%, rgba(201,169,110,0.05) 0%, transparent 50%);
  pointer-events: none;
}

/* ── Responsive ──────────────────────────────────────── */
@media (max-width: 960px) {
  .hamburger { display: flex; }
  .desktop-nav { display: none; }
}

@media (max-width: 480px) {
  .logo__en { font-size: 16px; }
  .logo__mark { width: 28px; height: 28px; }
  .mobile-menu__link { font-size: 20px; }
}
</style>
