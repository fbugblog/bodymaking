<template>
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

      <nav class="nav" :class="{ 'nav--open': menuOpen }">
        <ul class="nav__list">
          <li v-for="(item, i) in nav" :key="item.href">
            <a :href="item.href" class="nav__link" @click="menuOpen = false">
              <span class="nav__link-num">{{ String(i+1).padStart(2,'0') }}</span>
              <span>{{ item.label }}</span>
            </a>
          </li>
        </ul>
        <a href="#contact" class="btn-glow nav__cta" @click="menuOpen = false">無料体験</a>
      </nav>

      <button class="hamburger" :class="{ active: menuOpen }" @click="menuOpen = !menuOpen" aria-label="menu">
        <span></span><span></span><span></span>
      </button>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
const isScrolled = ref(false)
const menuOpen = ref(false)
const nav = [
  { href: '#about', label: 'About' },
  { href: '#classes', label: 'Classes' },
  { href: '#features', label: 'Why Us' },
  { href: '#schedule', label: 'Schedule' },
  { href: '#contact', label: 'Contact' },
]
const onScroll = () => { isScrolled.value = window.scrollY > 60 }
onMounted(() => window.addEventListener('scroll', onScroll))
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>

<style scoped>
.header {
  position: fixed;
  top: 0; left: 0; width: 100%;
  z-index: 200;
  padding: 24px 0;
  transition: padding .4s var(--ease-expo), background .4s;
}
.header.scrolled {
  padding: 14px 0;
  background: rgba(6, 4, 8, 0.85);
  backdrop-filter: blur(20px) saturate(180%);
  border-bottom: 1px solid rgba(233, 30, 140, 0.08);
}

.header__inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo {
  display: flex;
  align-items: center;
  gap: 12px;
}
.logo__mark {
  width: 36px; height: 36px;
  animation: rotateMark 12s linear infinite;
}
@keyframes rotateMark {
  to { transform: rotate(360deg); }
}
.logo__text { display: flex; flex-direction: column; line-height: 1.1; }
.logo__en {
  font-family: var(--font-serif);
  font-size: 18px;
  font-weight: 400;
  letter-spacing: 0.06em;
  background: linear-gradient(90deg, #fff 0%, rgba(255,255,255,.7) 100%);
  -webkit-background-clip: text; background-clip: text;
  -webkit-text-fill-color: transparent;
}
.logo__ja {
  font-size: 9px;
  letter-spacing: 0.12em;
  color: var(--gray);
}

/* Nav */
.nav {
  display: flex;
  align-items: center;
  gap: 36px;
}
.nav__list {
  display: flex;
  align-items: center;
  gap: 32px;
  list-style: none;
}
.nav__link {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 12px;
  letter-spacing: 0.1em;
  color: rgba(255,255,255,0.55);
  transition: color .3s;
  position: relative;
}
.nav__link::after {
  content: '';
  position: absolute;
  bottom: -4px; left: 0;
  width: 0; height: 1px;
  background: linear-gradient(90deg, var(--pink), var(--gold));
  transition: width .4s var(--ease-expo);
}
.nav__link:hover { color: white; }
.nav__link:hover::after { width: 100%; }
.nav__link-num {
  font-family: var(--font-serif);
  font-size: 9px;
  font-weight: 300;
  color: var(--pink-light);
  opacity: 0.5;
}

.nav__cta { font-size: 12px; padding: 10px 28px; }

/* Hamburger */
.hamburger {
  display: none;
  flex-direction: column;
  gap: 6px;
  padding: 6px;
  z-index: 300;
}
.hamburger span {
  display: block;
  width: 26px; height: 1px;
  background: white;
  transform-origin: center;
  transition: all .35s var(--ease-expo);
}
.hamburger.active span:nth-child(1) { transform: translateY(7px) rotate(45deg); }
.hamburger.active span:nth-child(2) { opacity: 0; transform: scaleX(0); }
.hamburger.active span:nth-child(3) { transform: translateY(-7px) rotate(-45deg); }

@media (max-width: 960px) {
  .hamburger { display: flex; }
  .nav {
    position: fixed;
    inset: 0;
    background: var(--deep);
    flex-direction: column;
    justify-content: center;
    gap: 48px;
    transform: translateX(100%);
    transition: transform .5s var(--ease-expo);
  }
  .nav--open { transform: translateX(0); }
  .nav__list { flex-direction: column; gap: 28px; }
  .nav__link { font-size: 20px; letter-spacing: 0.08em; color: rgba(255,255,255,.7); }
  .nav__cta { font-size: 16px; padding: 14px 48px; }
}
</style>
