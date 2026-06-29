<template>
  <section id="contact" class="contact">
    <!-- Diagonal accent -->
    <div class="contact__accent" aria-hidden="true"></div>

    <div class="container contact__inner">
      <!-- Left info -->
      <div class="contact__info">
        <p class="s-label reveal">Contact</p>
        <h2 class="contact__title reveal reveal-delay-1">
          お問い合わせ・<br />
          <em class="grad-text">無料体験申込</em>
        </h2>
        <p class="contact__text reveal reveal-delay-2">
          体験レッスンは随時受け付けています。<br />
          まずはお気軽にご連絡ください。
        </p>

        <div class="contact__details">
          <div class="contact__detail reveal" v-for="(d, i) in details" :key="d.label" :class="`reveal-delay-${i+2}`">
            <div class="contact__detail-icon">{{ d.icon }}</div>
            <div>
              <span class="contact__detail-label">{{ d.label }}</span>
              <span class="contact__detail-value">{{ d.value }}</span>
            </div>
          </div>
        </div>

        <!-- Decorative number -->
        <div class="contact__deco" aria-hidden="true">01</div>
      </div>

      <!-- Right form -->
      <div class="contact__form-wrap reveal--right reveal">
        <div class="form-card">
          <div class="form-card__glow"></div>
          <form @submit.prevent="submit" class="form">
            <div class="form-row form-row--2">
              <div class="form-field">
                <input id="name" v-model="f.name" type="text" required placeholder=" " class="form-input" />
                <label for="name" class="form-label">お名前 <span class="req">*</span></label>
                <div class="form-line"></div>
              </div>
              <div class="form-field">
                <input id="email" v-model="f.email" type="email" required placeholder=" " class="form-input" />
                <label for="email" class="form-label">メールアドレス <span class="req">*</span></label>
                <div class="form-line"></div>
              </div>
            </div>

            <div class="form-field">
              <select id="class" v-model="f.cls" class="form-input form-select" :class="{ 'has-value': f.cls }">
                <option value="" disabled selected></option>
                <option v-for="c in options" :key="c" :value="c">{{ c }}</option>
              </select>
              <label for="class" class="form-label">ご希望のクラス</label>
              <div class="form-line"></div>
            </div>

            <div class="form-field">
              <textarea id="msg" v-model="f.msg" placeholder=" " class="form-input form-textarea" rows="4"></textarea>
              <label for="msg" class="form-label">メッセージ</label>
              <div class="form-line"></div>
            </div>

            <button type="submit" class="form-submit" :class="{ done: submitted }">
              <span class="form-submit__text" v-if="!submitted">送信する</span>
              <span class="form-submit__text form-submit__done" v-else>送信しました ✓</span>
              <span class="form-submit__shine"></span>
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive } from 'vue'
const submitted = ref(false)
const f = reactive({ name:'', email:'', cls:'', msg:'' })
const details = [
  { icon: '📍', label: '住所', value: '東京都渋谷区〇〇 1-2-3' },
  { icon: '📞', label: '電話', value: '03-XXXX-XXXX' },
  { icon: '🕐', label: '受付時間', value: '月〜土 10:00〜20:00' },
]
const options = ['新体操ジュニア（基礎）','新体操ジュニア（中級）','競技クラス','ボディメイキング','大人の新体操','その他']

function submit() {
  submitted.value = true
  setTimeout(() => {
    submitted.value = false
    Object.assign(f, { name:'', email:'', cls:'', msg:'' })
  }, 3000)
}
</script>

<style scoped>
.contact {
  padding: clamp(80px, 10vw, 160px) 0;
  background: var(--black);
  position: relative;
  overflow: hidden;
}

.contact__accent {
  position: absolute;
  top: 0; right: 0;
  width: 50%;
  height: 100%;
  background: radial-gradient(ellipse at 100% 50%, rgba(233,30,140,0.05) 0%, transparent 60%);
  pointer-events: none;
}

.contact__inner {
  display: grid;
  grid-template-columns: 1fr 1.1fr;
  gap: 80px;
  align-items: start;
  position: relative;
  z-index: 1;
}

.contact__title {
  font-family: var(--font-serif);
  font-size: clamp(28px, 3.5vw, 52px);
  font-weight: 300;
  line-height: 1.3;
  margin-bottom: 24px;
}
.contact__title em { font-style: italic; }

.contact__text {
  font-size: 14px;
  line-height: 2;
  color: rgba(255,255,255,0.5);
  margin-bottom: 48px;
}

.contact__details { display: flex; flex-direction: column; gap: 24px; }
.contact__detail {
  display: flex;
  align-items: flex-start;
  gap: 18px;
}
.contact__detail-icon {
  width: 40px; height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(233,30,140,0.08);
  border: 1px solid rgba(233,30,140,0.12);
  border-radius: 10px;
  font-size: 16px;
  flex-shrink: 0;
}
.contact__detail-label {
  display: block;
  font-size: 10px;
  letter-spacing: 0.15em;
  color: rgba(255,255,255,0.25);
  text-transform: uppercase;
  margin-bottom: 3px;
}
.contact__detail-value {
  font-size: 14px;
  font-weight: 500;
  color: rgba(255,255,255,0.8);
}

.contact__deco {
  font-family: var(--font-serif);
  font-size: clamp(120px, 15vw, 200px);
  font-weight: 700;
  color: transparent;
  -webkit-text-stroke: 1px rgba(233,30,140,0.06);
  position: absolute;
  bottom: -40px;
  left: -20px;
  pointer-events: none;
  user-select: none;
  letter-spacing: -0.05em;
}

/* Form card */
.form-card {
  position: relative;
  background: var(--surface);
  border: 1px solid rgba(255,255,255,0.07);
  border-radius: 28px;
  padding: 52px 48px;
  overflow: hidden;
}
.form-card__glow {
  position: absolute;
  top: -40%; right: -20%;
  width: 400px; height: 400px;
  background: radial-gradient(circle, rgba(233,30,140,0.08) 0%, transparent 70%);
  pointer-events: none;
}

.form { display: flex; flex-direction: column; gap: 32px; }
.form-row--2 { display: grid; grid-template-columns: 1fr 1fr; gap: 28px; }

.form-field {
  position: relative;
  padding-top: 20px;
}
.form-input {
  width: 100%;
  padding: 14px 0 10px;
  font-size: 14px;
  font-family: var(--font-sans);
  color: white;
  background: transparent;
  border: none;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
}
.form-input::placeholder { color: transparent; }
.form-input option { background: var(--surface-2); color: white; }

.form-select { cursor: pointer; }
.form-select:not(.has-value) { color: transparent; }
.form-select.has-value { color: white; }

.form-textarea {
  resize: vertical;
  min-height: 100px;
  line-height: 1.7;
}

.form-label {
  position: absolute;
  top: 34px;
  left: 0;
  font-size: 14px;
  color: rgba(255,255,255,0.3);
  transition: all .25s var(--ease-expo);
  pointer-events: none;
  letter-spacing: 0.02em;
}
.req { color: var(--pink); font-size: 10px; }

.form-input:focus ~ .form-label,
.form-input:not(:placeholder-shown) ~ .form-label,
.form-input.has-value ~ .form-label,
.form-select.has-value ~ .form-label {
  top: 0;
  font-size: 10px;
  letter-spacing: 0.12em;
  color: var(--pink-light);
}

.form-line {
  position: absolute;
  bottom: 0; left: 0;
  width: 100%; height: 1px;
  background: rgba(255,255,255,0.08);
}
.form-line::after {
  content: '';
  position: absolute;
  bottom: 0; left: 0;
  width: 0; height: 1px;
  background: linear-gradient(90deg, var(--pink), var(--gold));
  transition: width .4s var(--ease-expo);
}
.form-field:focus-within .form-line::after { width: 100%; }

.form-submit {
  position: relative;
  width: 100%;
  padding: 18px;
  background: linear-gradient(135deg, var(--pink-dark), var(--pink));
  color: white;
  font-size: 14px;
  font-weight: 600;
  letter-spacing: 0.12em;
  border-radius: 14px;
  overflow: hidden;
  transition: transform .3s var(--ease-back), box-shadow .3s, opacity .3s;
  box-shadow: 0 8px 32px rgba(233,30,140,0.25);
}
.form-submit:hover {
  transform: translateY(-2px);
  box-shadow: 0 16px 48px rgba(233,30,140,0.4);
}
.form-submit.done {
  background: linear-gradient(135deg, #1a6b3a, #22c55e);
  box-shadow: 0 8px 32px rgba(34,197,94,0.25);
}
.form-submit__shine {
  position: absolute;
  top: -50%; left: -60%;
  width: 40%; height: 200%;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.15), transparent);
  transform: skewX(-20deg);
  animation: shimmer 3s ease-in-out infinite 1s;
}
@keyframes shimmer {
  0%   { left: -60%; }
  100% { left: 130%; }
}
.form-submit__text { position: relative; z-index: 1; }

@media (max-width: 960px) {
  .contact__inner { grid-template-columns: 1fr; gap: 48px; }
  .contact__deco { display: none; }
  .form-row--2 { grid-template-columns: 1fr; }
  .form-card { padding: 32px 24px; }
  .contact__text { margin-bottom: 32px; }
}

@media (max-width: 480px) {
  .form-card { padding: 28px 20px; }
  .form-submit { font-size: 13px; padding: 16px; }
}
</style>
