<template>
  <footer class="footer">
    <!-- Top marquee -->
    <div class="footer__marquee">
      <div class="marquee">
        <div class="marquee__track">
          <span v-for="n in 10" :key="n" class="footer__marquee-item">
            Studio Grace <em>✦</em> ボディメイキング <em>✦</em> 新体操 <em>◆</em>
          </span>
        </div>
      </div>
    </div>

    <div class="container">
      <div class="footer__inner">
        <div class="footer__brand">
          <p class="footer__logo">Studio Grace</p>
          <p class="footer__tagline">ボディメイキング・新体操教室</p>
          <p class="footer__copy-phrase">美しい体と動きを、あなたに。</p>
        </div>

        <nav class="footer__nav">
          <div v-for="col in navCols" :key="col.h" class="footer__nav-col">
            <p class="footer__nav-head">{{ col.h }}</p>
            <ul>
              <li v-for="item in col.items" :key="item.label">
                <a :href="item.href" class="footer__nav-link">{{ item.label }}</a>
              </li>
            </ul>
          </div>
        </nav>

        <div class="footer__side">
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
          <a href="#contact" class="footer__cta btn-glow">無料体験申込</a>
        </div>
      </div>

      <div class="footer__bottom">
        <p class="footer__copy">&copy; {{ year }} Studio Grace. All rights reserved.</p>
        <div class="footer__bottom-links">
          <a href="#">プライバシーポリシー</a>
          <a href="#">特定商取引法</a>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
const year = new Date().getFullYear()
const navCols = [
  { h: 'Menu', items: [
    { href: '#about', label: 'About' },
    { href: '#classes', label: 'Classes' },
    { href: '#features', label: 'Why Us' },
    { href: '#schedule', label: 'Schedule' },
  ]},
  { h: 'Classes', items: [
    { href: '#classes', label: '新体操ジュニア' },
    { href: '#classes', label: '競技クラス' },
    { href: '#classes', label: 'ボディメイキング' },
    { href: '#classes', label: '大人の新体操' },
  ]},
  { h: 'Info', items: [
    { href: '#contact', label: '無料体験申込' },
    { href: '#contact', label: 'お問い合わせ' },
    { href: '#', label: 'アクセス' },
    { href: '#', label: 'よくある質問' },
  ]},
]
</script>

<style scoped>
.footer {
  background: var(--deep);
  border-top: 1px solid rgba(255,255,255,0.04);
  padding-bottom: 0;
}

.footer__marquee {
  padding: 18px 0;
  border-bottom: 1px solid rgba(255,255,255,0.04);
  overflow: hidden;
}
.footer__marquee-item {
  font-family: var(--font-serif);
  font-size: 13px;
  font-weight: 300;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.07);
  padding: 0 24px;
  display: inline-flex;
  align-items: center;
  gap: 16px;
  white-space: nowrap;
}
.footer__marquee-item em {
  font-style: italic;
  color: rgba(233,30,140,0.2);
}

.footer__inner {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr;
  gap: 60px;
  padding: 72px 0 60px;
  align-items: start;
}

.footer__logo {
  font-family: var(--font-serif);
  font-size: 28px;
  font-weight: 300;
  letter-spacing: 0.06em;
  background: linear-gradient(90deg, white, rgba(255,255,255,0.5));
  -webkit-background-clip: text; background-clip: text;
  -webkit-text-fill-color: transparent;
  margin-bottom: 8px;
}
.footer__tagline {
  font-size: 10px;
  letter-spacing: 0.12em;
  color: rgba(255,255,255,0.2);
  margin-bottom: 16px;
}
.footer__copy-phrase {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 14px;
  font-weight: 300;
  color: var(--pink-light);
  opacity: 0.6;
}

.footer__nav {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 32px;
}
.footer__nav-head {
  font-family: var(--font-serif);
  font-size: 10px;
  font-weight: 300;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.2);
  margin-bottom: 18px;
}
.footer__nav-head + ul { list-style: none; display: flex; flex-direction: column; gap: 10px; }
.footer__nav-link {
  font-size: 13px;
  color: rgba(255,255,255,0.35);
  transition: color .25s;
  letter-spacing: 0.02em;
}
.footer__nav-link:hover { color: var(--pink-light); }

.footer__side {
  display: flex;
  flex-direction: column;
  gap: 24px;
  align-items: flex-end;
}
.footer__sns {
  display: flex;
  gap: 12px;
}
.footer__sns-link {
  width: 40px; height: 40px;
  border-radius: 50%;
  border: 1px solid rgba(255,255,255,0.08);
  display: flex;
  align-items: center;
  justify-content: center;
  color: rgba(255,255,255,0.3);
  transition: all .3s;
}
.footer__sns-link:hover {
  border-color: var(--pink);
  color: var(--pink-light);
}
.footer__sns-link svg { width: 16px; height: 16px; }
.footer__cta { font-size: 12px; padding: 12px 28px; }

.footer__bottom {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 24px 0;
  border-top: 1px solid rgba(255,255,255,0.05);
}
.footer__copy {
  font-size: 11px;
  color: rgba(255,255,255,0.15);
  letter-spacing: 0.06em;
}
.footer__bottom-links {
  display: flex;
  gap: 24px;
}
.footer__bottom-links a {
  font-size: 11px;
  color: rgba(255,255,255,0.2);
  transition: color .25s;
}
.footer__bottom-links a:hover { color: rgba(255,255,255,0.5); }

@media (max-width: 960px) {
  .footer__inner {
    grid-template-columns: 1fr;
    gap: 40px;
    padding: 48px 0;
  }
  .footer__side { align-items: flex-start; }
  .footer__bottom { flex-direction: column; gap: 16px; }
}
</style>
