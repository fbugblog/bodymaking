<template>
  <section id="classes" class="classes">
    <div class="container">
      <div class="classes__header">
        <p class="section-label">Our Classes</p>
        <h2 class="section-title">クラス一覧</h2>
        <p class="classes__subtitle">目的・レベルに合わせて選べる多彩なプログラムをご用意しています。</p>
      </div>

      <div class="classes__grid">
        <article
          class="class-card"
          v-for="cls in classes"
          :key="cls.id"
          :class="`class-card--${cls.color}`"
        >
          <div class="class-card__header">
            <span class="class-card__icon">{{ cls.icon }}</span>
            <span class="class-card__tag">{{ cls.tag }}</span>
          </div>
          <h3 class="class-card__title">{{ cls.title }}</h3>
          <p class="class-card__en">{{ cls.titleEn }}</p>
          <p class="class-card__desc">{{ cls.desc }}</p>
          <ul class="class-card__points">
            <li v-for="point in cls.points" :key="point">{{ point }}</li>
          </ul>
          <div class="class-card__footer">
            <div class="class-card__info">
              <span class="class-card__info-item">
                <svg viewBox="0 0 16 16" fill="none"><circle cx="8" cy="8" r="6" stroke="currentColor" stroke-width="1.2"/><path d="M8 5v3.5l2 1.5" stroke="currentColor" stroke-width="1.2" stroke-linecap="round"/></svg>
                {{ cls.duration }}
              </span>
              <span class="class-card__info-item">
                <svg viewBox="0 0 16 16" fill="none"><path d="M3 13c0-2.8 2.2-5 5-5s5 2.2 5 5" stroke="currentColor" stroke-width="1.2" stroke-linecap="round"/><circle cx="8" cy="5" r="2.5" stroke="currentColor" stroke-width="1.2"/></svg>
                {{ cls.target }}
              </span>
            </div>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
const classes = [
  {
    id: 1,
    icon: '🎀',
    tag: '人気No.1',
    color: 'pink',
    title: '新体操ジュニア',
    titleEn: 'Rhythmic Gymnastics Junior',
    desc: '基礎体力とリズム感を養いながら、新体操の美しい動きを習得します。手具（ロープ・フープ・ボール）を使った演技も学べます。',
    points: ['柔軟性・体幹強化', '手具操作の基礎', '発表会への参加'],
    duration: '60分 / 回',
    target: '4〜12歳',
  },
  {
    id: 2,
    icon: '✨',
    tag: '競技志向',
    color: 'gold',
    title: '新体操競技クラス',
    titleEn: 'Competitive Class',
    desc: '大会出場を目指すクラスです。技術の向上はもちろん、精神面での成長も重視した本格的なトレーニングを行います。',
    points: ['大会出場サポート', '個別フィードバック', '振付・表現力指導'],
    duration: '90分 / 回',
    target: '6歳〜',
  },
  {
    id: 3,
    icon: '💪',
    tag: 'ダイエット・美容',
    color: 'dark',
    title: 'ボディメイキング',
    titleEn: 'Body Making',
    desc: '新体操の動きをベースにした全身トレーニング。美しい姿勢・体幹・柔軟性を同時に鍛え、引き締まったボディラインを目指します。',
    points: ['姿勢矯正・体幹強化', '全身の柔軟性向上', '美しいボディライン'],
    duration: '60分 / 回',
    target: '中学生〜大人',
  },
  {
    id: 4,
    icon: '🌸',
    tag: '大人向け',
    color: 'light',
    title: '大人の新体操',
    titleEn: 'Adult Rhythmic Gymnastics',
    desc: '経験ゼロから始められる大人向けクラス。優雅な動きとしなやかな体を手に入れながら、心も豊かになる時間を過ごせます。',
    points: ['初心者歓迎', 'ストレス解消・リフレッシュ', '美しい所作の習得'],
    duration: '60分 / 回',
    target: '18歳〜',
  },
]
</script>

<style scoped>
.classes {
  padding: var(--section-padding) 0;
  background: white;
}

.classes__header {
  text-align: center;
  margin-bottom: 64px;
}

.section-label {
  font-family: var(--font-serif);
  font-size: 12px;
  font-weight: 300;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--pink-500);
  margin-bottom: 16px;
  display: block;
}

.section-title {
  font-family: var(--font-serif);
  font-size: clamp(28px, 3vw, 42px);
  font-weight: 300;
  letter-spacing: 0.04em;
  color: var(--gray-900);
  margin-bottom: 16px;
}

.classes__subtitle {
  font-size: 15px;
  color: var(--gray-500, #737373);
  max-width: 480px;
  margin: 0 auto;
  line-height: 1.8;
}

.classes__grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 24px;
}

.class-card {
  border-radius: 24px;
  padding: 36px;
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  gap: 12px;
  transition: transform var(--transition-base), box-shadow var(--transition-base);
}

.class-card:hover {
  transform: translateY(-4px);
}

.class-card--pink {
  background: linear-gradient(135deg, var(--pink-50) 0%, white 100%);
  border: 1px solid var(--pink-100);
  box-shadow: 0 4px 24px rgba(236, 72, 153, 0.06);
}
.class-card--pink:hover {
  box-shadow: 0 12px 40px rgba(236, 72, 153, 0.12);
}

.class-card--gold {
  background: linear-gradient(135deg, var(--gold-100) 0%, white 100%);
  border: 1px solid var(--gold-200);
  box-shadow: 0 4px 24px rgba(245, 166, 35, 0.06);
}
.class-card--gold:hover {
  box-shadow: 0 12px 40px rgba(245, 166, 35, 0.12);
}

.class-card--dark {
  background: linear-gradient(135deg, #1a0a12 0%, #2d0d20 100%);
  color: white;
}
.class-card--dark:hover {
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.2);
}

.class-card--light {
  background: linear-gradient(135deg, var(--pink-100) 0%, var(--pink-50) 100%);
  border: 1px solid var(--pink-200);
  box-shadow: 0 4px 24px rgba(236, 72, 153, 0.08);
}
.class-card--light:hover {
  box-shadow: 0 12px 40px rgba(236, 72, 153, 0.14);
}

.class-card__header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 8px;
}

.class-card__icon {
  font-size: 32px;
}

.class-card__tag {
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 0.08em;
  padding: 4px 12px;
  border-radius: 20px;
  background: rgba(236, 72, 153, 0.12);
  color: var(--pink-600);
}

.class-card--dark .class-card__tag {
  background: rgba(255, 255, 255, 0.12);
  color: var(--pink-300);
}

.class-card--gold .class-card__tag {
  background: rgba(245, 166, 35, 0.15);
  color: var(--gold-600);
}

.class-card__title {
  font-family: var(--font-serif);
  font-size: 22px;
  font-weight: 400;
  letter-spacing: 0.02em;
  line-height: 1.3;
}

.class-card__en {
  font-family: var(--font-serif);
  font-size: 12px;
  font-weight: 300;
  letter-spacing: 0.1em;
  opacity: 0.5;
  margin-top: -8px;
}

.class-card__desc {
  font-size: 14px;
  line-height: 1.9;
  opacity: 0.75;
  flex: 1;
}

.class-card__points {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 6px;
  margin: 8px 0;
}

.class-card__points li {
  font-size: 13px;
  padding-left: 16px;
  position: relative;
  opacity: 0.8;
}

.class-card__points li::before {
  content: '—';
  position: absolute;
  left: 0;
  color: var(--pink-400);
  font-size: 10px;
}

.class-card--dark .class-card__points li::before {
  color: var(--pink-300);
}

.class-card__footer {
  margin-top: 8px;
  padding-top: 16px;
  border-top: 1px solid rgba(0,0,0,0.06);
}

.class-card--dark .class-card__footer {
  border-top-color: rgba(255,255,255,0.1);
}

.class-card__info {
  display: flex;
  gap: 20px;
}

.class-card__info-item {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 12px;
  opacity: 0.65;
}

.class-card__info-item svg {
  width: 14px;
  height: 14px;
  flex-shrink: 0;
}

@media (max-width: 768px) {
  .classes__grid {
    grid-template-columns: 1fr;
  }

  .class-card {
    padding: 28px;
  }
}
</style>
