<template>
  <footer class="footer">
    <div class="container">
      <div class="footer__inner">
        <div class="footer__brand">
          <span class="footer__logo">Studio Grace</span>
          <p class="footer__tagline">ボディメイキング・新体操教室</p>
          <p class="footer__copy-text">美しい体と動きを、あなたに。</p>
        </div>

        <nav class="footer__nav">
          <div class="footer__nav-col" v-for="col in navCols" :key="col.heading">
            <p class="footer__nav-heading">{{ col.heading }}</p>
            <ul>
              <li v-for="item in col.items" :key="item.label">
                <a :href="item.href" class="footer__nav-link">{{ item.label }}</a>
              </li>
            </ul>
          </div>
        </nav>
      </div>

      <div class="footer__bottom">
        <p class="footer__copy">&copy; {{ year }} Studio Grace. All rights reserved.</p>
        <div class="footer__sns">
          <a href="#" class="footer__sns-link" aria-label="Instagram">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
              <rect x="2" y="2" width="20" height="20" rx="5"/>
              <circle cx="12" cy="12" r="4"/>
              <circle cx="17.5" cy="6.5" r="0.5" fill="currentColor" stroke="none"/>
            </svg>
          </a>
          <a href="#" class="footer__sns-link" aria-label="LINE">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
              <path d="M20.5 10.5c0-4.14-4.25-7.5-9.5-7.5S1.5 6.36 1.5 10.5c0 3.71 3.36 6.82 7.9 7.41.31.07.73.21.83.48.1.25.06.63.03.88l-.13.8c-.04.24-.18.93.82.51 1-.42 5.36-3.15 7.32-5.4 1.35-1.48 2.23-3.15 2.23-4.68z"/>
            </svg>
          </a>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
const year = new Date().getFullYear()

const navCols = [
  {
    heading: 'Menu',
    items: [
      { href: '#about', label: 'About' },
      { href: '#classes', label: 'クラス一覧' },
      { href: '#features', label: '選ばれる理由' },
      { href: '#schedule', label: 'スケジュール' },
    ],
  },
  {
    heading: 'Classes',
    items: [
      { href: '#classes', label: '新体操ジュニア' },
      { href: '#classes', label: '競技クラス' },
      { href: '#classes', label: 'ボディメイキング' },
      { href: '#classes', label: '大人の新体操' },
    ],
  },
  {
    heading: 'Info',
    items: [
      { href: '#contact', label: '無料体験申込' },
      { href: '#contact', label: 'お問い合わせ' },
      { href: '#', label: 'アクセス' },
      { href: '#', label: 'よくある質問' },
    ],
  },
]
</script>

<style scoped>
.footer {
  background: var(--gray-900);
  color: white;
  padding: 72px 0 32px;
}

.footer__inner {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 80px;
  margin-bottom: 60px;
}

.footer__brand {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.footer__logo {
  font-family: var(--font-serif);
  font-size: 26px;
  font-weight: 300;
  letter-spacing: 0.06em;
  color: white;
}

.footer__tagline {
  font-size: 11px;
  letter-spacing: 0.1em;
  color: rgba(255,255,255,0.4);
  margin-bottom: 12px;
}

.footer__copy-text {
  font-family: var(--font-serif);
  font-size: 14px;
  font-style: italic;
  color: var(--pink-300);
  font-weight: 300;
}

.footer__nav {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 32px;
}

.footer__nav-heading {
  font-family: var(--font-serif);
  font-size: 11px;
  font-weight: 300;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.35);
  margin-bottom: 16px;
}

.footer__nav-heading + ul {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.footer__nav-link {
  font-size: 13px;
  color: rgba(255,255,255,0.55);
  transition: color var(--transition-fast);
  letter-spacing: 0.02em;
}

.footer__nav-link:hover {
  color: var(--pink-300);
}

.footer__bottom {
  border-top: 1px solid rgba(255,255,255,0.06);
  padding-top: 28px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.footer__copy {
  font-size: 12px;
  color: rgba(255,255,255,0.25);
  letter-spacing: 0.04em;
}

.footer__sns {
  display: flex;
  gap: 16px;
}

.footer__sns-link {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  border: 1px solid rgba(255,255,255,0.1);
  display: flex;
  align-items: center;
  justify-content: center;
  color: rgba(255,255,255,0.4);
  transition: all var(--transition-base);
}

.footer__sns-link:hover {
  border-color: var(--pink-400);
  color: var(--pink-400);
}

.footer__sns-link svg {
  width: 16px;
  height: 16px;
}

@media (max-width: 768px) {
  .footer__inner {
    grid-template-columns: 1fr;
    gap: 48px;
  }

  .footer__nav {
    grid-template-columns: repeat(2, 1fr);
  }

  .footer__bottom {
    flex-direction: column;
    gap: 20px;
    text-align: center;
  }
}
</style>
