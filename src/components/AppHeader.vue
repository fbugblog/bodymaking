<template>
  <header class="header" :class="{ 'header--scrolled': isScrolled }">
    <div class="container header__inner">
      <a href="#top" class="header__logo">
        <span class="header__logo-en">Studio Grace</span>
        <span class="header__logo-ja">ボディメイキング・新体操教室</span>
      </a>

      <nav class="header__nav" :class="{ 'header__nav--open': isMenuOpen }">
        <ul class="header__nav-list">
          <li v-for="item in navItems" :key="item.href">
            <a :href="item.href" class="header__nav-link" @click="closeMenu">{{ item.label }}</a>
          </li>
        </ul>
        <a href="#contact" class="btn btn--outline header__nav-cta" @click="closeMenu">無料体験申込</a>
      </nav>

      <button class="header__hamburger" :class="{ 'header__hamburger--open': isMenuOpen }" @click="toggleMenu" aria-label="メニュー">
        <span></span>
        <span></span>
        <span></span>
      </button>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const isMenuOpen = ref(false)

const navItems = [
  { href: '#about', label: 'About' },
  { href: '#classes', label: 'クラス' },
  { href: '#features', label: '特徴' },
  { href: '#schedule', label: 'スケジュール' },
  { href: '#contact', label: 'お問い合わせ' },
]

function toggleMenu() {
  isMenuOpen.value = !isMenuOpen.value
}

function closeMenu() {
  isMenuOpen.value = false
}

function handleScroll() {
  isScrolled.value = window.scrollY > 40
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 100;
  padding: 20px 0;
  transition: background var(--transition-base), box-shadow var(--transition-base), padding var(--transition-base);
}

.header--scrolled {
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(12px);
  box-shadow: 0 1px 0 rgba(0,0,0,0.06);
  padding: 12px 0;
}

.header__inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 24px;
}

.header__logo {
  display: flex;
  flex-direction: column;
  line-height: 1.2;
}

.header__logo-en {
  font-family: var(--font-serif);
  font-size: 22px;
  font-weight: 600;
  letter-spacing: 0.04em;
  color: var(--color-primary);
}

.header__logo-ja {
  font-size: 10px;
  font-weight: 300;
  letter-spacing: 0.08em;
  color: var(--gray-600);
  margin-top: 1px;
}

.header__nav {
  display: flex;
  align-items: center;
  gap: 32px;
}

.header__nav-list {
  display: flex;
  align-items: center;
  gap: 28px;
  list-style: none;
}

.header__nav-link {
  font-size: 13px;
  font-weight: 500;
  letter-spacing: 0.06em;
  color: var(--gray-700, #404040);
  position: relative;
  padding-bottom: 2px;
  transition: color var(--transition-fast);
}

.header__nav-link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 1px;
  background: var(--color-primary);
  transition: width var(--transition-base);
}

.header__nav-link:hover {
  color: var(--color-primary);
}

.header__nav-link:hover::after {
  width: 100%;
}

.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 10px 24px;
  font-size: 13px;
  font-weight: 500;
  letter-spacing: 0.08em;
  border-radius: 40px;
  transition: all var(--transition-base);
  white-space: nowrap;
}

.btn--outline {
  border: 1.5px solid var(--color-primary);
  color: var(--color-primary);
}

.btn--outline:hover {
  background: var(--color-primary);
  color: white;
}

.header__hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  padding: 4px;
}

.header__hamburger span {
  display: block;
  width: 24px;
  height: 1.5px;
  background: var(--gray-800);
  transition: all var(--transition-base);
  transform-origin: center;
}

.header__hamburger--open span:nth-child(1) {
  transform: translateY(6.5px) rotate(45deg);
}
.header__hamburger--open span:nth-child(2) {
  opacity: 0;
}
.header__hamburger--open span:nth-child(3) {
  transform: translateY(-6.5px) rotate(-45deg);
}

@media (max-width: 900px) {
  .header__hamburger {
    display: flex;
  }

  .header__nav {
    position: fixed;
    inset: 0;
    background: white;
    flex-direction: column;
    justify-content: center;
    gap: 40px;
    transform: translateX(100%);
    transition: transform var(--transition-base);
  }

  .header__nav--open {
    transform: translateX(0);
  }

  .header__nav-list {
    flex-direction: column;
    gap: 24px;
  }

  .header__nav-link {
    font-size: 18px;
  }

  .header__nav-cta {
    font-size: 15px;
    padding: 14px 40px;
  }
}
</style>
