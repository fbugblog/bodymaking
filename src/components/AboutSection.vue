<template>
  <section id="about" class="about">
    <div class="container">
      <div class="about__inner">
        <div class="about__visual">
          <div class="about__card about__card--main">
            <div class="about__card-icon">
              <svg viewBox="0 0 60 60" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="30" cy="20" r="10" stroke="currentColor" stroke-width="1.5"/>
                <path d="M15 45 C15 35 22 28 30 28 C38 28 45 35 45 45" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
                <path d="M8 38 C8 30 14 24 22 24" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" opacity="0.5"/>
                <path d="M52 38 C52 30 46 24 38 24" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" opacity="0.5"/>
              </svg>
            </div>
            <p class="about__card-text">少人数制で<br />丁寧な指導</p>
          </div>
          <div class="about__card about__card--sub1">
            <span class="about__card-num">10+</span>
            <span class="about__card-desc">種類のクラス</span>
          </div>
          <div class="about__card about__card--sub2">
            <span class="about__card-accent">✦</span>
            <span>全国大会<br />入賞実績</span>
          </div>
          <div class="about__deco-circle"></div>
        </div>

        <div class="about__content">
          <p class="section-label">About Studio Grace</p>
          <h2 class="section-title">
            体を動かすことを<br />
            <em>もっと楽しく、美しく。</em>
          </h2>
          <p class="about__text">
            Studio Graceは、ボディメイキングと新体操を専門とする教室です。子どもから大人まで、それぞれの目標に合わせたプログラムを提供しています。
          </p>
          <p class="about__text">
            経験豊富なコーチ陣が、基礎から丁寧に指導。美しい姿勢と体幹を鍛えながら、しなやかな動きを習得できます。競技志向の方から、健康・美容目的の方まで幅広く対応しています。
          </p>
          <div class="about__values">
            <div class="about__value" v-for="v in values" :key="v.title">
              <span class="about__value-icon">{{ v.icon }}</span>
              <div>
                <strong class="about__value-title">{{ v.title }}</strong>
                <p class="about__value-desc">{{ v.desc }}</p>
              </div>
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
  padding: var(--section-padding) 0;
  background: var(--pink-50);
  overflow: hidden;
}

.about__inner {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: center;
}

/* Visual */
.about__visual {
  position: relative;
  height: 500px;
}

.about__card {
  position: absolute;
  background: white;
  border-radius: 20px;
  box-shadow: 0 8px 40px rgba(0,0,0,0.06);
  padding: 28px;
}

.about__card--main {
  top: 0;
  left: 0;
  right: 20%;
  bottom: 20%;
  background: linear-gradient(135deg, var(--pink-600) 0%, var(--pink-800) 100%);
  color: white;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  gap: 16px;
}

.about__card-icon {
  width: 52px;
  height: 52px;
  background: rgba(255,255,255,0.15);
  border-radius: 14px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.about__card-icon svg {
  width: 32px;
  height: 32px;
  color: white;
}

.about__card-text {
  font-family: var(--font-serif);
  font-size: 22px;
  font-weight: 300;
  line-height: 1.4;
  letter-spacing: 0.04em;
}

.about__card--sub1 {
  bottom: 0;
  right: 0;
  width: 48%;
  height: 35%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 4px;
}

.about__card-num {
  font-family: var(--font-serif);
  font-size: 48px;
  font-weight: 300;
  color: var(--pink-600);
  line-height: 1;
}

.about__card-desc {
  font-size: 12px;
  color: var(--gray-600);
  letter-spacing: 0.06em;
}

.about__card--sub2 {
  top: 45%;
  right: 0;
  width: 44%;
  height: 24%;
  display: flex;
  align-items: center;
  gap: 12px;
  font-size: 13px;
  font-weight: 500;
  line-height: 1.5;
  color: var(--gray-700, #404040);
}

.about__card-accent {
  color: var(--gold-400);
  font-size: 18px;
  flex-shrink: 0;
}

.about__deco-circle {
  position: absolute;
  width: 200px;
  height: 200px;
  border-radius: 50%;
  border: 1px solid var(--pink-200);
  bottom: -40px;
  left: -40px;
  pointer-events: none;
}

/* Content */
.about__content {
  padding: 20px 0;
}

.section-label {
  font-family: var(--font-serif);
  font-size: 12px;
  font-weight: 300;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--pink-500);
  margin-bottom: 20px;
}

.section-title {
  font-family: var(--font-serif);
  font-size: clamp(28px, 3vw, 42px);
  font-weight: 300;
  line-height: 1.4;
  letter-spacing: 0.02em;
  color: var(--gray-900);
  margin-bottom: 28px;
}

.section-title em {
  font-style: italic;
  color: var(--pink-600);
  font-weight: 300;
}

.about__text {
  font-size: 15px;
  line-height: 2;
  color: var(--gray-600);
  margin-bottom: 20px;
}

.about__values {
  display: flex;
  flex-direction: column;
  gap: 20px;
  margin-top: 36px;
}

.about__value {
  display: flex;
  align-items: flex-start;
  gap: 16px;
}

.about__value-icon {
  color: var(--pink-400);
  font-size: 14px;
  margin-top: 2px;
  flex-shrink: 0;
}

.about__value-title {
  font-size: 14px;
  font-weight: 600;
  display: block;
  margin-bottom: 2px;
  color: var(--gray-800);
}

.about__value-desc {
  font-size: 13px;
  color: var(--gray-500, #737373);
  line-height: 1.6;
}

@media (max-width: 900px) {
  .about__inner {
    grid-template-columns: 1fr;
    gap: 60px;
  }

  .about__visual {
    height: 340px;
    max-width: 400px;
    margin: 0 auto;
  }
}
</style>
