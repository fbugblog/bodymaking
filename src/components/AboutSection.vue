<template>
  <section id="about" class="about">
    <!-- Big decorative text -->
    <div class="about__deco-text" aria-hidden="true">GRACE</div>

    <div class="container about__inner">
      <!-- Left: visual grid -->
      <div class="about__grid reveal--left reveal">
        <div class="about__card about__card--main">
          <div class="about__card-bg"></div>
          <div class="about__card-content">
            <p class="about__card-num grad-text">15</p>
            <p class="about__card-unit">Years</p>
            <p class="about__card-desc">of Excellence</p>
          </div>
        </div>

        <div class="about__card about__card--top">
          <div class="about__card-label">在籍生徒数</div>
          <div class="about__card-big">200<span class="plus">+</span></div>
        </div>

        <div class="about__card about__card--mid">
          <div class="about__icon-row">
            <span class="icon">🏆</span>
            <span class="icon">🥇</span>
            <span class="icon">🌸</span>
          </div>
          <p>全国大会<br/>入賞実績</p>
        </div>

        <div class="about__card about__card--bot reveal reveal-delay-2">
          <div class="about__progress-label">継続率</div>
          <div class="about__progress-bar">
            <div class="about__progress-fill"></div>
          </div>
          <div class="about__progress-val">98%</div>
        </div>

        <!-- Decorative lines -->
        <div class="about__cross" aria-hidden="true"></div>
      </div>

      <!-- Right: text -->
      <div class="about__text-col">
        <p class="s-label reveal">About Studio Grace</p>
        <h2 class="about__title reveal reveal-delay-1">
          体を動かすことを<br />
          もっと<span class="grad-text">楽しく、</span><br />
          <em class="about__title-em">美しく。</em>
        </h2>
        <p class="about__body reveal reveal-delay-2">
          Studio Graceは、ボディメイキングと新体操を専門とする教室です。子どもから大人まで、それぞれの目標に合わせたプログラムを提供しています。
        </p>
        <p class="about__body reveal reveal-delay-3">
          経験豊富なコーチ陣が基礎から丁寧に指導。美しい姿勢と体幹を鍛えながら、しなやかな動きを習得できます。
        </p>

        <div class="about__values">
          <div class="about__value reveal" v-for="(v, i) in values" :key="v.title" :class="`reveal-delay-${i+2}`">
            <div class="about__value-icon">{{ v.icon }}</div>
            <div>
              <strong class="about__value-title">{{ v.title }}</strong>
              <p class="about__value-desc">{{ v.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const values = [
  { icon: '◈', title: '専門性の高い指導', desc: '新体操経験者・指導者資格保有コーチが担当' },
  { icon: '◈', title: '個人に合わせたプログラム', desc: '体力・技術レベルに応じた個別カリキュラム' },
  { icon: '◈', title: '温かいコミュニティ', desc: '仲間と共に成長できる安心・安全な環境' },
]
</script>

<style scoped>
.about {
  position: relative;
  padding: clamp(100px, 12vw, 160px) 0;
  background: var(--deep);
  overflow: hidden;
}

.about__deco-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-family: var(--font-serif);
  font-size: clamp(120px, 18vw, 260px);
  font-weight: 700;
  letter-spacing: 0.1em;
  color: transparent;
  -webkit-text-stroke: 1px rgba(233,30,140,0.05);
  pointer-events: none;
  white-space: nowrap;
  user-select: none;
}

.about__inner {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: center;
  position: relative;
  z-index: 1;
}

/* Card grid */
.about__grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: auto auto auto;
  gap: 12px;
  position: relative;
}

.about__card {
  background: var(--surface);
  border: 1px solid rgba(255,255,255,0.06);
  border-radius: 20px;
  padding: 28px;
  transition: border-color .3s, transform .4s var(--ease-expo);
  position: relative;
  overflow: hidden;
}
.about__card:hover {
  border-color: rgba(233,30,140,0.25);
  transform: translateY(-4px);
}

.about__card--main {
  grid-column: 1;
  grid-row: 1 / 3;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  gap: 4px;
  min-height: 220px;
  background: linear-gradient(160deg, #1E0818 0%, #0D0610 100%);
  border-color: rgba(233,30,140,0.12);
}
.about__card-bg {
  position: absolute;
  inset: 0;
  background: radial-gradient(circle at 30% 70%, rgba(233,30,140,0.15) 0%, transparent 65%);
  pointer-events: none;
}
.about__card-content { position: relative; }
.about__card-num {
  font-family: var(--font-serif);
  font-size: 72px;
  font-weight: 300;
  line-height: 1;
  letter-spacing: -0.02em;
}
.about__card-unit {
  font-family: var(--font-serif);
  font-size: 18px;
  font-weight: 300;
  color: rgba(255,255,255,0.4);
  letter-spacing: 0.1em;
}
.about__card-desc {
  font-size: 11px;
  letter-spacing: 0.1em;
  color: rgba(255,255,255,0.25);
  text-transform: uppercase;
}

.about__card--top {
  grid-column: 2;
  grid-row: 1;
  display: flex;
  flex-direction: column;
  gap: 4px;
}
.about__card-label {
  font-size: 10px;
  letter-spacing: 0.15em;
  color: rgba(255,255,255,0.3);
  text-transform: uppercase;
}
.about__card-big {
  font-family: var(--font-serif);
  font-size: 48px;
  font-weight: 300;
  color: white;
  line-height: 1;
}
.plus { font-size: 28px; color: var(--pink); }

.about__card--mid {
  grid-column: 2;
  grid-row: 2;
  font-size: 13px;
  line-height: 1.6;
  color: rgba(255,255,255,0.6);
}
.about__icon-row {
  display: flex;
  gap: 6px;
  margin-bottom: 10px;
  font-size: 20px;
}

.about__card--bot {
  grid-column: 1 / 3;
  grid-row: 3;
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 20px 28px;
}
.about__progress-label {
  font-size: 11px;
  letter-spacing: 0.12em;
  color: rgba(255,255,255,0.3);
  white-space: nowrap;
}
.about__progress-bar {
  flex: 1;
  height: 3px;
  background: rgba(255,255,255,0.06);
  border-radius: 2px;
  overflow: hidden;
}
.about__progress-fill {
  height: 100%;
  width: 0;
  background: linear-gradient(90deg, var(--pink-dark), var(--pink), var(--gold));
  border-radius: 2px;
  transition: width 1.4s var(--ease-expo);
}
.about__card--bot.is-visible .about__progress-fill {
  width: 98%;
}
@keyframes progressIn {
  from { width: 0; }
}
.about__progress-val {
  font-family: var(--font-serif);
  font-size: 22px;
  font-weight: 300;
  color: var(--pink-light);
}

.about__cross {
  position: absolute;
  top: 50%; left: 50%;
  transform: translate(-50%, -50%);
  width: 16px; height: 16px;
  pointer-events: none;
}
.about__cross::before,
.about__cross::after {
  content: '';
  position: absolute;
  background: rgba(233,30,140,0.2);
}
.about__cross::before { width: 1px; height: 100%; left: 50%; }
.about__cross::after  { width: 100%; height: 1px; top: 50%; }

/* Text column */
.about__title {
  font-family: var(--font-serif);
  font-size: clamp(30px, 3.5vw, 52px);
  font-weight: 300;
  line-height: 1.3;
  letter-spacing: 0.02em;
  margin-bottom: 28px;
}
.about__title-em {
  font-style: italic;
  display: block;
  color: rgba(255,255,255,0.5);
}

.about__body {
  font-size: 14px;
  line-height: 2;
  color: rgba(255,255,255,0.5);
  margin-bottom: 16px;
}

.about__values {
  margin-top: 36px;
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding-top: 36px;
  border-top: 1px solid rgba(255,255,255,0.06);
}
.about__value {
  display: flex;
  gap: 16px;
  align-items: flex-start;
}
.about__value-icon {
  color: var(--pink);
  font-size: 14px;
  margin-top: 2px;
  flex-shrink: 0;
}
.about__value-title {
  display: block;
  font-size: 13px;
  font-weight: 600;
  color: rgba(255,255,255,0.85);
  margin-bottom: 3px;
}
.about__value-desc {
  font-size: 12px;
  color: rgba(255,255,255,0.35);
  line-height: 1.6;
}

@media (max-width: 960px) {
  .about__inner { grid-template-columns: 1fr; gap: 48px; }
  .about__grid { max-width: 480px; margin: 0 auto; width: 100%; }
  .about__deco-text { font-size: clamp(80px, 20vw, 160px); }
}

@media (max-width: 480px) {
  .about__card--main { min-height: 160px; }
  .about__card-num { font-size: 52px; }
  .about__card-big { font-size: 36px; }
  .about__grid { gap: 8px; }
}
</style>
