<template>
  <section id="top" class="hero">
    <!-- Mesh gradient bg -->
    <div class="hero__mesh" aria-hidden="true">
      <div class="mesh-orb mesh-orb--1"></div>
      <div class="mesh-orb mesh-orb--2"></div>
      <div class="mesh-orb mesh-orb--3"></div>
      <div class="mesh-orb mesh-orb--4"></div>
      <div class="hero__grid-lines"></div>
    </div>

    <div class="container hero__inner">
      <!-- Left: content -->
      <div class="hero__content">
        <div class="hero__eyebrow reveal">
          <span class="hero__eyebrow-line"></span>
          <span>Body Making &amp; Rhythmic Gymnastics</span>
        </div>

        <h1 class="hero__title">
          <span class="hero__title-row reveal reveal-delay-1">
            <em class="hero__title-em">美しい</em>体と
          </span>
          <span class="hero__title-row reveal reveal-delay-2">
            しなやかな
          </span>
          <span class="hero__title-row reveal reveal-delay-3">
            動きを <em class="hero__title-accent">あなたに。</em>
          </span>
        </h1>

        <p class="hero__sub reveal reveal-delay-4">
          ボディメイキングと新体操の技術を融合させた<br />
          独自プログラムで、内側から輝く美しさを追求します。
        </p>

        <div class="hero__actions reveal reveal-delay-5">
          <a href="#contact" class="btn-glow">
            無料体験レッスン
            <svg viewBox="0 0 20 20" fill="none" width="16"><path d="M4 10h12M11 5l5 5-5 5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/></svg>
          </a>
          <a href="#classes" class="btn-ghost">クラスを見る</a>
        </div>

        <!-- Stats -->
        <div class="hero__stats reveal">
          <div class="hero__stat" v-for="s in stats" :key="s.label">
            <span class="hero__stat-val">{{ s.val }}</span>
            <span class="hero__stat-label">{{ s.label }}</span>
          </div>
        </div>
      </div>

      <!-- Right: visual -->
      <div class="hero__visual reveal--right reveal">
        <div class="hero__frame">
          <div class="hero__frame-inner">
            <div class="hero__ribbon ribbon-1">Rhythmic</div>
            <div class="hero__ribbon ribbon-2">Grace</div>
            <!-- Silhouette -->
            <svg class="hero__fig" viewBox="0 0 320 480" fill="none">
              <defs>
                <radialGradient id="figGrad" cx="50%" cy="30%" r="60%">
                  <stop offset="0%" stop-color="#FF6BC1" stop-opacity="0.9"/>
                  <stop offset="100%" stop-color="#E91E8C" stop-opacity="0.4"/>
                </radialGradient>
                <filter id="glow">
                  <feGaussianBlur stdDeviation="3" result="blur"/>
                  <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
                </filter>
              </defs>
              <!-- Head -->
              <ellipse cx="160" cy="56" rx="28" ry="28" fill="url(#figGrad)" filter="url(#glow)"/>
              <!-- Body -->
              <path d="M160 84 C145 100 130 120 125 155 L145 158 C148 132 155 115 160 105 C165 115 172 132 175 158 L195 155 C190 120 175 100 160 84Z" fill="url(#figGrad)" filter="url(#glow)"/>
              <!-- Arms arabesque -->
              <path d="M130 120 C105 108 78 95 48 82" stroke="url(#figGrad)" stroke-width="12" stroke-linecap="round" filter="url(#glow)"/>
              <path d="M48 82 C32 74 15 78 5 66" stroke="#C9A96E" stroke-width="6" stroke-linecap="round" opacity="0.6"/>
              <!-- Ribbon -->
              <path d="M5 66 C-8 54 2 40 18 46 C34 52 28 70 40 76 C52 82 62 72 58 58 C54 44 38 42 30 52" stroke="#C9A96E" stroke-width="2.5" fill="none" stroke-linecap="round" opacity="0.8"/>
              <path d="M190 120 C210 115 225 118 232 130" stroke="url(#figGrad)" stroke-width="12" stroke-linecap="round" filter="url(#glow)"/>
              <!-- Legs -->
              <path d="M145 158 C138 200 134 250 136 310" stroke="url(#figGrad)" stroke-width="14" stroke-linecap="round" filter="url(#glow)"/>
              <path d="M175 158 C185 185 200 210 225 235 C248 256 266 258 278 244" stroke="url(#figGrad)" stroke-width="14" stroke-linecap="round" filter="url(#glow)"/>
              <!-- Pointed foot -->
              <path d="M278 244 C288 236 290 224 282 218" stroke="url(#figGrad)" stroke-width="10" stroke-linecap="round" filter="url(#glow)"/>
              <!-- Sparkles -->
              <circle cx="60" cy="80" r="2" fill="#C9A96E" opacity="0.8">
                <animate attributeName="opacity" values="0.8;0.2;0.8" dur="2s" repeatCount="indefinite"/>
              </circle>
              <circle cx="250" cy="200" r="2.5" fill="#FF6BC1" opacity="0.7">
                <animate attributeName="opacity" values="0.7;0.1;0.7" dur="2.5s" repeatCount="indefinite"/>
              </circle>
              <circle cx="130" cy="300" r="1.5" fill="#C9A96E" opacity="0.6">
                <animate attributeName="opacity" values="0.6;0.2;0.6" dur="1.8s" repeatCount="indefinite"/>
              </circle>
            </svg>
          </div>

          <!-- Corner decorations -->
          <div class="hero__frame-corner hero__frame-corner--tl"></div>
          <div class="hero__frame-corner hero__frame-corner--tr"></div>
          <div class="hero__frame-corner hero__frame-corner--bl"></div>
          <div class="hero__frame-corner hero__frame-corner--br"></div>

          <!-- Floating badges -->
          <div class="hero__badge badge-a">
            <span class="badge-icon">✦</span>
            <span class="badge-text">新体操</span>
          </div>
          <div class="hero__badge badge-b">
            <span class="badge-icon">✦</span>
            <span class="badge-text">Body Making</span>
          </div>
          <div class="hero__badge badge-c">
            <span>15年の<br/>指導実績</span>
          </div>
        </div>
      </div>
    </div>

    <!-- Scroll indicator -->
    <a href="#about" class="hero__scroll">
      <span class="scroll-text">Scroll</span>
      <span class="scroll-track"><span class="scroll-dot"></span></span>
    </a>
  </section>
</template>

<script setup>
const stats = [
  { val: '200+', label: '在籍生徒数' },
  { val: '15年', label: '指導実績' },
  { val: '98%', label: '継続率' },
]
</script>

<style scoped>
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  overflow: hidden;
  padding-top: 90px;
}

/* Mesh background */
.hero__mesh {
  position: absolute;
  inset: 0;
  z-index: 0;
  background: var(--deep);
}
.mesh-orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(100px);
  opacity: 0.5;
  animation: orbFloat 12s ease-in-out infinite;
}
.mesh-orb--1 {
  width: 700px; height: 700px;
  top: -200px; right: -150px;
  background: radial-gradient(circle, rgba(233,30,140,0.35) 0%, transparent 70%);
  animation-duration: 10s;
}
.mesh-orb--2 {
  width: 500px; height: 500px;
  bottom: -100px; left: 0;
  background: radial-gradient(circle, rgba(201,169,110,0.2) 0%, transparent 70%);
  animation-duration: 14s;
  animation-delay: -4s;
}
.mesh-orb--3 {
  width: 400px; height: 400px;
  top: 30%; left: 30%;
  background: radial-gradient(circle, rgba(168,0,94,0.18) 0%, transparent 70%);
  animation-duration: 16s;
  animation-delay: -7s;
}
.mesh-orb--4 {
  width: 300px; height: 300px;
  top: 10%; left: 15%;
  background: radial-gradient(circle, rgba(233,30,140,0.12) 0%, transparent 70%);
  animation-duration: 8s;
  animation-delay: -2s;
}
@keyframes orbFloat {
  0%, 100% { transform: translate(0, 0) scale(1); }
  33%       { transform: translate(-40px, 30px) scale(1.08); }
  66%       { transform: translate(30px, -40px) scale(0.94); }
}
.hero__grid-lines {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(255,255,255,0.02) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,0.02) 1px, transparent 1px);
  background-size: 80px 80px;
  mask-image: radial-gradient(ellipse at center, black 20%, transparent 80%);
}

/* Layout */
.hero__inner {
  position: relative;
  z-index: 1;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
  min-height: calc(100vh - 90px);
  padding-top: 40px;
  padding-bottom: 100px;
}

/* Content */
.hero__eyebrow {
  display: flex;
  align-items: center;
  gap: 14px;
  font-size: 10px;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: var(--pink-light);
  margin-bottom: 36px;
}
.hero__eyebrow-line {
  display: block;
  width: 40px; height: 1px;
  background: linear-gradient(90deg, var(--pink), transparent);
}

.hero__title {
  font-family: var(--font-serif);
  font-size: clamp(46px, 5.5vw, 80px);
  font-weight: 300;
  line-height: 1.15;
  letter-spacing: 0.01em;
  margin-bottom: 32px;
  display: flex;
  flex-direction: column;
  gap: 2px;
}
.hero__title-row { display: block; }
.hero__title-em {
  font-style: italic;
  background: linear-gradient(135deg, #FF6BC1, #E91E8C);
  -webkit-background-clip: text; background-clip: text;
  -webkit-text-fill-color: transparent;
}
.hero__title-accent {
  font-style: italic;
  background: linear-gradient(135deg, var(--gold-light), var(--gold));
  -webkit-background-clip: text; background-clip: text;
  -webkit-text-fill-color: transparent;
}

.hero__sub {
  font-size: 14px;
  line-height: 2;
  color: rgba(255,255,255,0.55);
  margin-bottom: 48px;
  max-width: 420px;
}

.hero__actions {
  display: flex;
  gap: 16px;
  margin-bottom: 64px;
  flex-wrap: wrap;
}

.hero__stats {
  display: flex;
  gap: 40px;
  padding-top: 32px;
  border-top: 1px solid rgba(255,255,255,0.07);
}
.hero__stat { display: flex; flex-direction: column; gap: 4px; }
.hero__stat-val {
  font-family: var(--font-serif);
  font-size: 32px;
  font-weight: 300;
  background: linear-gradient(135deg, white, rgba(255,255,255,0.6));
  -webkit-background-clip: text; background-clip: text;
  -webkit-text-fill-color: transparent;
  line-height: 1;
}
.hero__stat-label {
  font-size: 10px;
  letter-spacing: 0.12em;
  color: rgba(255,255,255,0.35);
}

/* Visual */
.hero__visual {
  display: flex;
  justify-content: center;
}
.hero__frame {
  position: relative;
  width: 100%;
  max-width: 400px;
  aspect-ratio: 3/4;
}
.hero__frame-inner {
  width: 100%;
  height: 100%;
  background: linear-gradient(145deg,
    rgba(233,30,140,0.08) 0%,
    rgba(201,169,110,0.04) 50%,
    rgba(233,30,140,0.06) 100%);
  border: 1px solid rgba(233,30,140,0.15);
  border-radius: 40% 60% 55% 45% / 45% 45% 55% 55%;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  backdrop-filter: blur(4px);
  animation: morphBorder 8s ease-in-out infinite;
}
@keyframes morphBorder {
  0%, 100% { border-radius: 40% 60% 55% 45% / 45% 45% 55% 55%; }
  25%       { border-radius: 55% 45% 45% 55% / 60% 40% 60% 40%; }
  50%       { border-radius: 45% 55% 60% 40% / 40% 60% 40% 60%; }
  75%       { border-radius: 60% 40% 40% 60% / 50% 55% 45% 50%; }
}

.hero__fig { width: 75%; height: auto; }

/* Ribbons */
.hero__ribbon {
  position: absolute;
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 11px;
  font-weight: 300;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.08);
  pointer-events: none;
}
.ribbon-1 { top: 12%; left: 8%; transform: rotate(-90deg); }
.ribbon-2 { bottom: 12%; right: 8%; transform: rotate(90deg); }

/* Corner decorations */
.hero__frame-corner {
  position: absolute;
  width: 24px; height: 24px;
  opacity: 0.4;
}
.hero__frame-corner--tl {
  top: -1px; left: -1px;
  border-top: 1px solid var(--pink);
  border-left: 1px solid var(--pink);
}
.hero__frame-corner--tr {
  top: -1px; right: -1px;
  border-top: 1px solid var(--gold);
  border-right: 1px solid var(--gold);
}
.hero__frame-corner--bl {
  bottom: -1px; left: -1px;
  border-bottom: 1px solid var(--gold);
  border-left: 1px solid var(--gold);
}
.hero__frame-corner--br {
  bottom: -1px; right: -1px;
  border-bottom: 1px solid var(--pink);
  border-right: 1px solid var(--pink);
}

/* Badges */
.hero__badge {
  position: absolute;
  display: flex;
  align-items: center;
  gap: 8px;
  background: rgba(13, 6, 16, 0.85);
  backdrop-filter: blur(16px) saturate(180%);
  border: 1px solid rgba(233,30,140,0.2);
  border-radius: 40px;
  padding: 10px 18px;
  font-size: 11px;
  letter-spacing: 0.08em;
  color: rgba(255,255,255,0.8);
  white-space: nowrap;
  animation: badgeFloat 5s ease-in-out infinite;
}
.badge-a { top: 12%; left: -32px; animation-delay: 0s; }
.badge-b { bottom: 22%; right: -32px; animation-delay: 1.5s; }
.badge-c {
  bottom: 5%; left: -20px;
  border-radius: 16px;
  font-size: 10px;
  line-height: 1.5;
  animation-delay: 3s;
}
.badge-icon { color: var(--gold); font-size: 9px; }
.badge-text { font-weight: 500; }
@keyframes badgeFloat {
  0%, 100% { transform: translateY(0); }
  50%       { transform: translateY(-8px); }
}

/* Scroll */
.hero__scroll {
  position: absolute;
  bottom: 48px; left: 50%;
  transform: translateX(-50%);
  z-index: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 14px;
}
.scroll-text {
  font-family: var(--font-serif);
  font-size: 9px;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.25);
  writing-mode: vertical-rl;
}
.scroll-track {
  width: 1px;
  height: 60px;
  background: rgba(255,255,255,0.08);
  position: relative;
  overflow: hidden;
}
.scroll-dot {
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 30%;
  background: linear-gradient(to bottom, transparent, var(--pink), transparent);
  animation: scrollDot 1.8s ease-in-out infinite;
}
@keyframes scrollDot {
  0%   { top: -30%; }
  100% { top: 130%; }
}

@media (max-width: 960px) {
  .hero__inner { grid-template-columns: 1fr; text-align: center; }
  .hero__eyebrow, .hero__stats { justify-content: center; }
  .hero__sub { margin-left: auto; margin-right: auto; }
  .hero__actions { justify-content: center; }
  .hero__visual { display: none; }
}
</style>
