<template>
  <section id="classes" class="classes">
    <div class="container">
      <div class="classes__header">
        <p class="s-label reveal">Our Classes</p>
        <h2 class="classes__title reveal reveal-delay-1">
          目的に合わせて選べる<br /><span class="grad-text">4つのクラス</span>
        </h2>
      </div>

      <div class="classes__grid">
        <article
          class="class-card reveal"
          :class="[`class-card--${c.theme}`, `reveal-delay-${i+1}`]"
          v-for="(c, i) in classes"
          :key="c.id"
          @mouseenter="hovered = i"
          @mouseleave="hovered = null"
        >
          <div class="class-card__bg" aria-hidden="true"></div>

          <!-- Index -->
          <span class="class-card__index">{{ String(c.id).padStart(2, '0') }}</span>

          <!-- Tag -->
          <span class="class-card__tag">{{ c.tag }}</span>

          <!-- Icon ring -->
          <div class="class-card__icon-wrap">
            <div class="class-card__icon-ring"></div>
            <span class="class-card__icon">{{ c.icon }}</span>
          </div>

          <h3 class="class-card__title">{{ c.title }}</h3>
          <p class="class-card__en">{{ c.en }}</p>
          <p class="class-card__desc">{{ c.desc }}</p>

          <ul class="class-card__list">
            <li v-for="p in c.points" :key="p">
              <span class="list-dot"></span>{{ p }}
            </li>
          </ul>

          <div class="class-card__footer">
            <div class="class-card__meta">
              <span>⏱ {{ c.duration }}</span>
              <span>👥 {{ c.target }}</span>
            </div>
            <a href="#contact" class="class-card__link">
              体験する
              <svg viewBox="0 0 16 16" fill="none" width="14"><path d="M3 8h10M9 4l4 4-4 4" stroke="currentColor" stroke-width="1.2" stroke-linecap="round"/></svg>
            </a>
          </div>
        </article>
      </div>
    </div>

    <!-- Bottom divider -->
    <div class="classes__divider" aria-hidden="true"></div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
const hovered = ref(null)

const classes = [
  {
    id: 1, icon: '🎀', tag: '人気No.1', theme: 'a',
    title: '新体操ジュニア', en: 'Rhythmic Gymnastics Junior',
    desc: '基礎体力とリズム感を養いながら、美しい新体操の動きを習得します。',
    points: ['柔軟性・体幹強化', '手具操作の基礎（ロープ・フープ・ボール）', '年2回の発表会参加'],
    duration: '60分', target: '4〜12歳',
  },
  {
    id: 2, icon: '🏅', tag: '競技志向', theme: 'b',
    title: '競技クラス', en: 'Competitive Class',
    desc: '大会出場を目指す本格的トレーニング。技術・精神面の両方を磨きます。',
    points: ['全国大会出場サポート', '個別フィードバック', '振付・表現力指導'],
    duration: '90分', target: '6歳〜',
  },
  {
    id: 3, icon: '✨', tag: 'ダイエット・美容', theme: 'c',
    title: 'ボディメイキング', en: 'Body Making',
    desc: '新体操ベースの全身トレーニング。姿勢・体幹・柔軟性を同時に改善。',
    points: ['姿勢矯正・体幹強化', '全身の柔軟性向上', '美しいボディライン'],
    duration: '60分', target: '中学生〜大人',
  },
  {
    id: 4, icon: '🌸', tag: '大人向け', theme: 'd',
    title: '大人の新体操', en: 'Adult Rhythmic Gymnastics',
    desc: '経験ゼロでも始められる大人専用クラス。優雅な動きと心の豊かさを。',
    points: ['初心者歓迎・丁寧指導', 'ストレス解消・リフレッシュ', '美しい所作の習得'],
    duration: '60分', target: '18歳〜',
  },
]
</script>

<style scoped>
.classes {
  padding: clamp(100px, 12vw, 160px) 0 0;
  background: var(--black);
  position: relative;
}

.classes__header {
  margin-bottom: 64px;
}
.classes__title {
  font-family: var(--font-serif);
  font-size: clamp(30px, 4vw, 56px);
  font-weight: 300;
  line-height: 1.3;
  letter-spacing: 0.02em;
}

.classes__grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1px;
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(255,255,255,0.04);
}

.class-card {
  position: relative;
  padding: 48px 40px;
  background: var(--black);
  display: flex;
  flex-direction: column;
  gap: 14px;
  overflow: hidden;
  transition: background .4s;
  isolation: isolate;
}
.class-card:hover { background: var(--surface); }
.class-card:hover .class-card__icon-ring { transform: scale(1.2) rotate(45deg); opacity: 1; }
.class-card:hover .class-card__bg { opacity: 1; }

.class-card__bg {
  position: absolute;
  inset: 0;
  opacity: 0;
  transition: opacity .5s;
  pointer-events: none;
}
.class-card--a .class-card__bg { background: radial-gradient(ellipse at 80% 20%, rgba(233,30,140,0.08) 0%, transparent 60%); }
.class-card--b .class-card__bg { background: radial-gradient(ellipse at 80% 20%, rgba(201,169,110,0.08) 0%, transparent 60%); }
.class-card--c .class-card__bg { background: radial-gradient(ellipse at 80% 20%, rgba(168,0,94,0.1) 0%, transparent 60%); }
.class-card--d .class-card__bg { background: radial-gradient(ellipse at 80% 20%, rgba(255,107,193,0.07) 0%, transparent 60%); }

.class-card__index {
  font-family: var(--font-serif);
  font-size: 11px;
  font-weight: 300;
  letter-spacing: 0.2em;
  color: rgba(255,255,255,0.15);
}

.class-card__tag {
  display: inline-block;
  font-size: 10px;
  letter-spacing: 0.1em;
  padding: 4px 12px;
  border-radius: 20px;
  align-self: flex-start;
}
.class-card--a .class-card__tag { background: rgba(233,30,140,0.15); color: var(--pink-light); }
.class-card--b .class-card__tag { background: rgba(201,169,110,0.15); color: var(--gold-light); }
.class-card--c .class-card__tag { background: rgba(168,0,94,0.2); color: #FF80C8; }
.class-card--d .class-card__tag { background: rgba(255,107,193,0.12); color: #FFB3DC; }

.class-card__icon-wrap {
  position: relative;
  width: 56px; height: 56px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.class-card__icon-ring {
  position: absolute;
  inset: 0;
  border-radius: 50%;
  border: 1px solid rgba(233,30,140,0.2);
  transition: transform .5s var(--ease-expo), opacity .3s;
  opacity: 0.4;
}
.class-card--b .class-card__icon-ring { border-color: rgba(201,169,110,0.3); }
.class-card__icon { font-size: 28px; position: relative; }

.class-card__title {
  font-family: var(--font-serif);
  font-size: 24px;
  font-weight: 400;
  letter-spacing: 0.02em;
}
.class-card__en {
  font-family: var(--font-serif);
  font-size: 11px;
  font-weight: 300;
  letter-spacing: 0.12em;
  color: rgba(255,255,255,0.2);
  margin-top: -10px;
}
.class-card__desc {
  font-size: 13px;
  line-height: 1.9;
  color: rgba(255,255,255,0.5);
  flex: 1;
}

.class-card__list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 7px;
}
.class-card__list li {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 12px;
  color: rgba(255,255,255,0.45);
}
.list-dot {
  width: 4px; height: 4px;
  border-radius: 50%;
  flex-shrink: 0;
}
.class-card--a .list-dot { background: var(--pink); }
.class-card--b .list-dot { background: var(--gold); }
.class-card--c .list-dot { background: #FF80C8; }
.class-card--d .list-dot { background: #FFB3DC; }

.class-card__footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-top: 20px;
  border-top: 1px solid rgba(255,255,255,0.05);
  margin-top: 4px;
}
.class-card__meta {
  display: flex;
  gap: 16px;
  font-size: 11px;
  color: rgba(255,255,255,0.25);
}
.class-card__link {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 12px;
  letter-spacing: 0.08em;
  color: rgba(255,255,255,0.4);
  transition: color .3s;
}
.class-card--a .class-card__link:hover { color: var(--pink-light); }
.class-card--b .class-card__link:hover { color: var(--gold-light); }
.class-card--c .class-card__link:hover { color: #FF80C8; }
.class-card--d .class-card__link:hover { color: #FFB3DC; }

.classes__divider {
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(233,30,140,0.15), rgba(201,169,110,0.15), transparent);
  margin-top: 0;
}

@media (max-width: 768px) {
  .classes__grid { grid-template-columns: 1fr; }
  .class-card { padding: 36px 28px; }
}
</style>
