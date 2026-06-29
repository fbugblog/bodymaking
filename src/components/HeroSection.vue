<template>
  <section id="top" class="hero">
    <div class="hero__bg">
      <div class="hero__gradient"></div>
      <div class="hero__shapes">
        <div class="hero__shape hero__shape--1"></div>
        <div class="hero__shape hero__shape--2"></div>
        <div class="hero__shape hero__shape--3"></div>
      </div>
    </div>

    <div class="container hero__inner">
      <div class="hero__content">
        <p class="hero__eyebrow">Body Making &amp; Rhythmic Gymnastics</p>
        <h1 class="hero__title">
          美しい体と<br />
          しなやかな動きを<br />
          <em>あなたに。</em>
        </h1>
        <p class="hero__subtitle">
          ボディメイキングと新体操の技術を融合させた<br class="pc-only" />
          独自のプログラムで、内側から輝く美しさを追求します。
        </p>
        <div class="hero__actions">
          <a href="#contact" class="btn btn--primary">無料体験レッスン</a>
          <a href="#classes" class="btn btn--ghost">クラスを見る</a>
        </div>
        <div class="hero__stats">
          <div class="hero__stat" v-for="stat in stats" :key="stat.label">
            <span class="hero__stat-value">{{ stat.value }}</span>
            <span class="hero__stat-label">{{ stat.label }}</span>
          </div>
        </div>
      </div>

      <div class="hero__visual">
        <div class="hero__image-wrap">
          <div class="hero__image-placeholder">
            <svg viewBox="0 0 400 500" fill="none" xmlns="http://www.w3.org/2000/svg" class="hero__silhouette">
              <!-- Gymnast silhouette (simplified elegant figure) -->
              <ellipse cx="200" cy="80" rx="32" ry="32" fill="white" opacity="0.9"/>
              <!-- Body -->
              <path d="M200 112 C180 130 160 155 155 190 L165 192 C168 165 185 143 200 128 C215 143 232 165 235 192 L245 190 C240 155 220 130 200 112Z" fill="white" opacity="0.85"/>
              <!-- Raised arm -->
              <path d="M165 145 C145 130 118 115 95 100" stroke="white" stroke-width="10" stroke-linecap="round" opacity="0.85"/>
              <!-- Ribbon -->
              <path d="M95 100 C75 88 50 92 30 78 C15 68 8 52 20 40 C32 28 50 38 58 55 C66 72 55 90 65 105 C72 116 88 112 95 100Z" stroke="var(--pink-300)" stroke-width="3" fill="none" opacity="0.8"/>
              <path d="M30 78 C18 70 5 74 2 62" stroke="var(--pink-300)" stroke-width="3" fill="none" opacity="0.6"/>
              <!-- Other arm -->
              <path d="M235 145 C252 148 260 155 255 168" stroke="white" stroke-width="10" stroke-linecap="round" opacity="0.85"/>
              <!-- Legs (arabesque pose) -->
              <path d="M165 192 C158 230 155 270 158 310" stroke="white" stroke-width="12" stroke-linecap="round" opacity="0.85"/>
              <path d="M235 192 C245 215 260 235 285 250 C305 262 320 260 330 248" stroke="white" stroke-width="12" stroke-linecap="round" opacity="0.85"/>
              <!-- Pointe foot -->
              <path d="M330 248 C338 242 342 234 336 228" stroke="white" stroke-width="8" stroke-linecap="round" opacity="0.85"/>
            </svg>
          </div>
          <div class="hero__badge hero__badge--1">
            <span class="hero__badge-icon">✦</span>
            <span>新体操</span>
          </div>
          <div class="hero__badge hero__badge--2">
            <span class="hero__badge-icon">✦</span>
            <span>ボディメイキング</span>
          </div>
        </div>
      </div>
    </div>

    <a href="#about" class="hero__scroll" aria-label="スクロールダウン">
      <span class="hero__scroll-text">Scroll</span>
      <span class="hero__scroll-line"></span>
    </a>
  </section>
</template>

<script setup>
const stats = [
  { value: '200+', label: '在籍生徒数' },
  { value: '15年', label: '指導実績' },
  { value: '98%', label: '継続率' },
]
</script>

<style scoped>
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  overflow: hidden;
  padding-top: 80px;
}

.hero__bg {
  position: absolute;
  inset: 0;
  z-index: 0;
}

.hero__gradient {
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg,
    #1a0a12 0%,
    #2d0d20 25%,
    #3d1230 50%,
    #1e0818 75%,
    #0d0408 100%
  );
}

.hero__shapes {
  position: absolute;
  inset: 0;
  overflow: hidden;
}

.hero__shape {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  opacity: 0.3;
}

.hero__shape--1 {
  width: 600px;
  height: 600px;
  top: -200px;
  right: -100px;
  background: radial-gradient(circle, #ec4899 0%, transparent 70%);
  animation: float1 8s ease-in-out infinite;
}

.hero__shape--2 {
  width: 400px;
  height: 400px;
  bottom: -100px;
  left: 10%;
  background: radial-gradient(circle, #f5a623 0%, transparent 70%);
  animation: float2 10s ease-in-out infinite;
}

.hero__shape--3 {
  width: 300px;
  height: 300px;
  top: 30%;
  left: 40%;
  background: radial-gradient(circle, #db2777 0%, transparent 70%);
  opacity: 0.2;
  animation: float1 12s ease-in-out infinite reverse;
}

@keyframes float1 {
  0%, 100% { transform: translate(0, 0) scale(1); }
  33% { transform: translate(-30px, 20px) scale(1.05); }
  66% { transform: translate(20px, -30px) scale(0.95); }
}

@keyframes float2 {
  0%, 100% { transform: translate(0, 0) scale(1); }
  50% { transform: translate(40px, -20px) scale(1.08); }
}

.hero__inner {
  position: relative;
  z-index: 1;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
  min-height: calc(100vh - 80px);
  padding-top: 60px;
  padding-bottom: 100px;
}

.hero__content {
  color: white;
}

.hero__eyebrow {
  font-family: var(--font-serif);
  font-size: 13px;
  font-weight: 300;
  letter-spacing: 0.2em;
  color: var(--pink-300);
  margin-bottom: 24px;
  text-transform: uppercase;
  opacity: 0.9;
}

.hero__title {
  font-family: var(--font-serif);
  font-size: clamp(42px, 5vw, 72px);
  font-weight: 300;
  line-height: 1.25;
  letter-spacing: 0.02em;
  margin-bottom: 28px;
}

.hero__title em {
  font-style: italic;
  color: var(--pink-300);
  font-weight: 400;
}

.hero__subtitle {
  font-size: 15px;
  font-weight: 300;
  line-height: 1.9;
  color: rgba(255, 255, 255, 0.7);
  margin-bottom: 48px;
  max-width: 440px;
}

.hero__actions {
  display: flex;
  gap: 16px;
  margin-bottom: 60px;
  flex-wrap: wrap;
}

.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 14px 32px;
  font-size: 14px;
  font-weight: 500;
  letter-spacing: 0.08em;
  border-radius: 40px;
  transition: all var(--transition-base);
  white-space: nowrap;
}

.btn--primary {
  background: linear-gradient(135deg, var(--pink-500), var(--pink-600));
  color: white;
  box-shadow: 0 8px 24px rgba(236, 72, 153, 0.4);
}

.btn--primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 12px 32px rgba(236, 72, 153, 0.5);
}

.btn--ghost {
  border: 1px solid rgba(255, 255, 255, 0.3);
  color: white;
}

.btn--ghost:hover {
  border-color: rgba(255, 255, 255, 0.6);
  background: rgba(255, 255, 255, 0.08);
}

.hero__stats {
  display: flex;
  gap: 40px;
}

.hero__stat {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.hero__stat-value {
  font-family: var(--font-serif);
  font-size: 28px;
  font-weight: 300;
  color: white;
  letter-spacing: 0.02em;
}

.hero__stat-label {
  font-size: 11px;
  letter-spacing: 0.1em;
  color: rgba(255, 255, 255, 0.5);
}

/* Visual */
.hero__visual {
  display: flex;
  justify-content: center;
  align-items: center;
}

.hero__image-wrap {
  position: relative;
  width: 100%;
  max-width: 420px;
  aspect-ratio: 4/5;
}

.hero__image-placeholder {
  width: 100%;
  height: 100%;
  background: linear-gradient(160deg,
    rgba(236, 72, 153, 0.15) 0%,
    rgba(245, 166, 35, 0.08) 100%
  );
  border-radius: 40% 60% 60% 40% / 40% 40% 60% 60%;
  border: 1px solid rgba(236, 72, 153, 0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  backdrop-filter: blur(4px);
}

.hero__silhouette {
  width: 80%;
  height: 80%;
  object-fit: contain;
  opacity: 0.9;
}

.hero__badge {
  position: absolute;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(12px);
  border: 1px solid rgba(255, 255, 255, 0.15);
  border-radius: 40px;
  padding: 10px 20px;
  color: white;
  font-size: 12px;
  font-weight: 500;
  letter-spacing: 0.06em;
  display: flex;
  align-items: center;
  gap: 8px;
  white-space: nowrap;
}

.hero__badge--1 {
  top: 15%;
  left: -20px;
}

.hero__badge--2 {
  bottom: 20%;
  right: -20px;
}

.hero__badge-icon {
  color: var(--gold-400);
  font-size: 10px;
}

/* Scroll indicator */
.hero__scroll {
  position: absolute;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
  color: rgba(255, 255, 255, 0.4);
  font-size: 10px;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  transition: color var(--transition-base);
}

.hero__scroll:hover {
  color: rgba(255, 255, 255, 0.7);
}

.hero__scroll-line {
  width: 1px;
  height: 50px;
  background: linear-gradient(to bottom, rgba(255,255,255,0.4), transparent);
  animation: scrollLine 2s ease-in-out infinite;
}

@keyframes scrollLine {
  0% { transform: scaleY(0); transform-origin: top; }
  50% { transform: scaleY(1); transform-origin: top; }
  51% { transform: scaleY(1); transform-origin: bottom; }
  100% { transform: scaleY(0); transform-origin: bottom; }
}

.pc-only {
  display: inline;
}

@media (max-width: 900px) {
  .hero__inner {
    grid-template-columns: 1fr;
    text-align: center;
    padding-top: 40px;
  }

  .hero__subtitle {
    margin-left: auto;
    margin-right: auto;
  }

  .hero__actions {
    justify-content: center;
  }

  .hero__stats {
    justify-content: center;
  }

  .hero__visual {
    display: none;
  }

  .pc-only {
    display: none;
  }
}
</style>
