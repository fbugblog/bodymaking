<template>
  <section id="features" class="features">
    <div class="container">
      <div class="features__header">
        <p class="section-label">Why Choose Us</p>
        <h2 class="section-title">Studio Graceが<br /><em>選ばれる理由</em></h2>
      </div>

      <div class="features__grid">
        <div class="feature-item" v-for="(feat, i) in features" :key="feat.title">
          <div class="feature-item__num">{{ String(i + 1).padStart(2, '0') }}</div>
          <div class="feature-item__icon">{{ feat.icon }}</div>
          <h3 class="feature-item__title">{{ feat.title }}</h3>
          <p class="feature-item__desc">{{ feat.desc }}</p>
        </div>
      </div>

      <div class="features__cta">
        <div class="features__cta-inner">
          <p class="features__cta-label">まずは気軽に体験から</p>
          <h3 class="features__cta-title">無料体験レッスン実施中</h3>
          <p class="features__cta-text">初めての方でも安心。インストラクターが丁寧にサポートします。</p>
          <a href="#contact" class="btn btn--primary">無料体験を申し込む</a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const features = [
  {
    icon: '🏆',
    title: '全国大会入賞実績',
    desc: '競技クラスの生徒は全国大会での入賞実績多数。本格的な指導を提供します。',
  },
  {
    icon: '👩‍🏫',
    title: '経験豊富なコーチ陣',
    desc: '元競技選手・指導者資格保有のコーチが在籍。一人ひとりに寄り添った指導を行います。',
  },
  {
    icon: '📐',
    title: '少人数制クラス',
    desc: '1クラス最大8名の少人数制。細やかな個別指導で確実な上達をサポートします。',
  },
  {
    icon: '🌟',
    title: '充実した施設',
    desc: '鏡張りの広いスタジオ・専用マット完備。安全で快適な環境でレッスンを行えます。',
  },
  {
    icon: '📅',
    title: '柔軟なスケジュール',
    desc: '平日・週末・夜間クラスを多数開講。お仕事や学校帰りにも通いやすい時間割。',
  },
  {
    icon: '💝',
    title: '発表会・イベント充実',
    desc: '年2回の発表会や合宿など、練習の成果を発揮できる機会を定期的に設けています。',
  },
]
</script>

<style scoped>
.features {
  padding: var(--section-padding) 0;
  background: var(--gray-900);
  position: relative;
  overflow: hidden;
}

.features::before {
  content: '';
  position: absolute;
  top: -200px;
  right: -200px;
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, rgba(236, 72, 153, 0.08) 0%, transparent 70%);
  border-radius: 50%;
  pointer-events: none;
}

.features__header {
  text-align: center;
  margin-bottom: 72px;
  color: white;
}

.section-label {
  font-family: var(--font-serif);
  font-size: 12px;
  font-weight: 300;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--pink-400);
  margin-bottom: 16px;
  display: block;
}

.section-title {
  font-family: var(--font-serif);
  font-size: clamp(28px, 3vw, 42px);
  font-weight: 300;
  letter-spacing: 0.04em;
  line-height: 1.4;
}

.section-title em {
  font-style: italic;
  color: var(--pink-400);
}

.features__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2px;
  margin-bottom: 80px;
}

.feature-item {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.06);
  padding: 40px 32px;
  position: relative;
  transition: background var(--transition-base);
}

.feature-item:hover {
  background: rgba(236, 72, 153, 0.06);
  border-color: rgba(236, 72, 153, 0.15);
}

.feature-item__num {
  font-family: var(--font-serif);
  font-size: 11px;
  font-weight: 300;
  letter-spacing: 0.2em;
  color: rgba(255, 255, 255, 0.2);
  margin-bottom: 20px;
}

.feature-item__icon {
  font-size: 28px;
  margin-bottom: 20px;
}

.feature-item__title {
  font-size: 16px;
  font-weight: 600;
  color: white;
  margin-bottom: 12px;
  letter-spacing: 0.02em;
}

.feature-item__desc {
  font-size: 13px;
  line-height: 1.9;
  color: rgba(255, 255, 255, 0.5);
}

/* CTA Banner */
.features__cta {
  background: linear-gradient(135deg, var(--pink-600) 0%, var(--pink-800) 50%, #6b0f3a 100%);
  border-radius: 28px;
  overflow: hidden;
  position: relative;
}

.features__cta::before {
  content: '';
  position: absolute;
  top: -60px;
  right: -60px;
  width: 200px;
  height: 200px;
  background: rgba(255,255,255,0.05);
  border-radius: 50%;
}

.features__cta::after {
  content: '';
  position: absolute;
  bottom: -80px;
  left: 10%;
  width: 250px;
  height: 250px;
  background: rgba(245, 166, 35, 0.08);
  border-radius: 50%;
}

.features__cta-inner {
  position: relative;
  z-index: 1;
  padding: 60px 80px;
  text-align: center;
  color: white;
}

.features__cta-label {
  font-family: var(--font-serif);
  font-size: 12px;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.6);
  margin-bottom: 16px;
}

.features__cta-title {
  font-family: var(--font-serif);
  font-size: clamp(24px, 3vw, 36px);
  font-weight: 300;
  letter-spacing: 0.04em;
  margin-bottom: 16px;
}

.features__cta-text {
  font-size: 14px;
  color: rgba(255,255,255,0.7);
  margin-bottom: 36px;
}

.btn--primary {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 16px 48px;
  background: white;
  color: var(--pink-600);
  font-size: 14px;
  font-weight: 600;
  letter-spacing: 0.1em;
  border-radius: 40px;
  transition: all var(--transition-base);
  box-shadow: 0 8px 32px rgba(0,0,0,0.2);
}

.btn--primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 12px 40px rgba(0,0,0,0.3);
}

@media (max-width: 900px) {
  .features__grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
  .features__grid {
    grid-template-columns: 1fr;
  }

  .features__cta-inner {
    padding: 48px 28px;
  }
}
</style>
