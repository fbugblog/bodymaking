<template>
  <section id="features" class="features">
    <!-- Background -->
    <div class="features__bg" aria-hidden="true">
      <div class="features__orb features__orb--1"></div>
      <div class="features__orb features__orb--2"></div>
      <div class="features__scan"></div>
    </div>

    <div class="container">
      <div class="features__top">
        <div class="features__top-left">
          <p class="s-label reveal">Why Choose Us</p>
          <h2 class="features__title reveal reveal-delay-1">
            Studio Graceが<br />
            <em class="grad-text">選ばれる理由</em>
          </h2>
        </div>
        <p class="features__top-text reveal reveal-delay-2">
          長年の指導実績と情熱を持つコーチ陣が、<br />
          あなたの成長をトータルサポートします。
        </p>
      </div>

      <div class="features__items">
        <div
          class="feat-item reveal"
          :class="`reveal-delay-${(i % 3) + 1}`"
          v-for="(f, i) in features"
          :key="f.title"
        >
          <div class="feat-item__head">
            <span class="feat-item__num">{{ String(i+1).padStart(2,'0') }}</span>
            <span class="feat-item__icon">{{ f.icon }}</span>
          </div>
          <h3 class="feat-item__title">{{ f.title }}</h3>
          <p class="feat-item__desc">{{ f.desc }}</p>
          <div class="feat-item__line"></div>
        </div>
      </div>

      <!-- CTA block -->
      <div class="features__cta reveal">
        <div class="features__cta-left">
          <p class="features__cta-sub">まずは気軽に体験から</p>
          <h3 class="features__cta-title">無料体験レッスン<br /><em>実施中</em></h3>
        </div>
        <div class="features__cta-right">
          <p class="features__cta-desc">
            初めての方でも安心。<br />
            インストラクターが丁寧にサポートします。
          </p>
          <a href="#contact" class="btn-glow">
            今すぐ申し込む
            <svg viewBox="0 0 20 20" fill="none" width="16"><path d="M4 10h12M11 5l5 5-5 5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/></svg>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const features = [
  { icon: '🏆', title: '全国大会入賞実績', desc: '競技クラスの生徒は全国大会での入賞実績多数。本格的な指導を受けられます。' },
  { icon: '👩‍🏫', title: '経験豊富なコーチ陣', desc: '元競技選手・指導者資格保有のコーチが在籍。一人ひとりに寄り添います。' },
  { icon: '📐', title: '少人数制クラス', desc: '1クラス最大8名の少人数制。細やかな個別指導で確実な上達を実現。' },
  { icon: '🏛️', title: '充実した専用施設', desc: '鏡張りの広いスタジオ・専用マット完備。安全で快適な環境で練習できます。' },
  { icon: '📅', title: '柔軟なスケジュール', desc: '平日・週末・夜間クラスを多数開講。ライフスタイルに合わせて通えます。' },
  { icon: '💝', title: '発表会・イベント充実', desc: '年2回の発表会や合宿など、練習の成果を発揮できる機会を定期的に提供。' },
]
</script>

<style scoped>
.features {
  padding: clamp(100px, 12vw, 160px) 0;
  background: var(--surface);
  position: relative;
  overflow: hidden;
}

/* Background effects */
.features__bg { position: absolute; inset: 0; pointer-events: none; }
.features__orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(120px);
}
.features__orb--1 {
  width: 600px; height: 600px;
  top: -200px; right: -200px;
  background: radial-gradient(circle, rgba(233,30,140,0.1) 0%, transparent 70%);
  animation: orbPulse 6s ease-in-out infinite;
}
.features__orb--2 {
  width: 500px; height: 500px;
  bottom: -150px; left: -150px;
  background: radial-gradient(circle, rgba(201,169,110,0.07) 0%, transparent 70%);
  animation: orbPulse 8s ease-in-out infinite 2s;
}
.features__scan {
  position: absolute;
  inset: 0;
  background: repeating-linear-gradient(
    0deg,
    transparent,
    transparent 79px,
    rgba(255,255,255,0.015) 80px
  );
}
@keyframes orbPulse {
  0%, 100% { transform: scale(1); opacity: 0.8; }
  50%       { transform: scale(1.15); opacity: 1; }
}

/* Top */
.features__top {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  align-items: end;
  margin-bottom: 80px;
}
.features__title {
  font-family: var(--font-serif);
  font-size: clamp(30px, 4vw, 56px);
  font-weight: 300;
  line-height: 1.3;
}
.features__title em { font-style: normal; }
.features__top-text {
  font-size: 14px;
  line-height: 2;
  color: rgba(255,255,255,0.45);
  max-width: 360px;
  align-self: center;
}

/* Feature items */
.features__items {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0;
  border-top: 1px solid rgba(255,255,255,0.06);
  margin-bottom: 80px;
}

.feat-item {
  padding: 40px 36px;
  border-right: 1px solid rgba(255,255,255,0.06);
  border-bottom: 1px solid rgba(255,255,255,0.06);
  position: relative;
  transition: background .3s;
  cursor: default;
}
.feat-item:nth-child(3n) { border-right: none; }
.feat-item:nth-child(4),
.feat-item:nth-child(5),
.feat-item:nth-child(6) { border-bottom: none; }
.feat-item:hover { background: rgba(233,30,140,0.04); }
.feat-item:hover .feat-item__line { width: 100%; }

.feat-item__head {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 20px;
}
.feat-item__num {
  font-family: var(--font-serif);
  font-size: 11px;
  letter-spacing: 0.2em;
  color: rgba(255,255,255,0.15);
}
.feat-item__icon { font-size: 24px; }
.feat-item__title {
  font-size: 15px;
  font-weight: 600;
  color: rgba(255,255,255,0.85);
  margin-bottom: 12px;
  letter-spacing: 0.02em;
}
.feat-item__desc {
  font-size: 13px;
  line-height: 1.9;
  color: rgba(255,255,255,0.4);
}
.feat-item__line {
  position: absolute;
  bottom: 0; left: 0;
  height: 1px; width: 0;
  background: linear-gradient(90deg, var(--pink), var(--gold));
  transition: width .6s var(--ease-expo);
}

/* CTA */
.features__cta {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
  background: linear-gradient(135deg,
    rgba(233,30,140,0.08) 0%,
    rgba(201,169,110,0.04) 50%,
    rgba(233,30,140,0.06) 100%);
  border: 1px solid rgba(233,30,140,0.15);
  border-radius: 28px;
  padding: 60px 80px;
  position: relative;
  overflow: hidden;
}
.features__cta::before {
  content: '';
  position: absolute;
  inset: 0;
  background: radial-gradient(ellipse at 0% 50%, rgba(233,30,140,0.12) 0%, transparent 60%);
  pointer-events: none;
}

.features__cta-sub {
  font-family: var(--font-serif);
  font-size: 11px;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  color: var(--pink-light);
  opacity: 0.7;
  margin-bottom: 16px;
}
.features__cta-title {
  font-family: var(--font-serif);
  font-size: clamp(26px, 3vw, 44px);
  font-weight: 300;
  line-height: 1.25;
  letter-spacing: 0.03em;
}
.features__cta-title em {
  font-style: italic;
  background: linear-gradient(135deg, var(--pink-light), var(--gold));
  -webkit-background-clip: text; background-clip: text;
  -webkit-text-fill-color: transparent;
}
.features__cta-desc {
  font-size: 14px;
  line-height: 2;
  color: rgba(255,255,255,0.5);
  margin-bottom: 32px;
}

@media (max-width: 960px) {
  .features__top { grid-template-columns: 1fr; gap: 20px; margin-bottom: 48px; }
  .features__items { grid-template-columns: repeat(2, 1fr); }
  .feat-item:nth-child(3n) { border-right: 1px solid rgba(255,255,255,0.06); }
  .feat-item:nth-child(2n) { border-right: none; }
  .feat-item:nth-child(5), .feat-item:nth-child(6) { border-bottom: none; }
  .feat-item:nth-child(4) { border-bottom: 1px solid rgba(255,255,255,0.06); }
  .features__cta { grid-template-columns: 1fr; gap: 32px; padding: 40px 32px; }
}

@media (max-width: 600px) {
  .features__items { grid-template-columns: 1fr; }
  .feat-item { border-right: none !important; padding: 32px 24px; }
  .feat-item:nth-child(n) { border-bottom: 1px solid rgba(255,255,255,0.06); }
  .feat-item:last-child { border-bottom: none; }
  .features__cta { padding: 32px 24px; border-radius: 20px; }
}
</style>
