<template>
  <section id="contact" class="contact">
    <div class="container">
      <div class="contact__inner">
        <div class="contact__info">
          <p class="section-label">Contact</p>
          <h2 class="section-title">お問い合わせ・<br /><em>無料体験申込</em></h2>
          <p class="contact__text">
            体験レッスンは随時受け付けています。<br />
            まずはお気軽にご連絡ください。
          </p>

          <div class="contact__details">
            <div class="contact__detail" v-for="d in details" :key="d.label">
              <span class="contact__detail-icon">{{ d.icon }}</span>
              <div>
                <span class="contact__detail-label">{{ d.label }}</span>
                <span class="contact__detail-value">{{ d.value }}</span>
              </div>
            </div>
          </div>
        </div>

        <div class="contact__form-wrap">
          <form class="contact__form" @submit.prevent="handleSubmit">
            <div class="form-group">
              <label class="form-label" for="name">お名前 <span class="form-required">必須</span></label>
              <input
                id="name"
                v-model="form.name"
                class="form-input"
                type="text"
                placeholder="山田 花子"
                required
              />
            </div>
            <div class="form-group">
              <label class="form-label" for="email">メールアドレス <span class="form-required">必須</span></label>
              <input
                id="email"
                v-model="form.email"
                class="form-input"
                type="email"
                placeholder="example@email.com"
                required
              />
            </div>
            <div class="form-group">
              <label class="form-label" for="class">ご希望のクラス</label>
              <select id="class" v-model="form.className" class="form-input form-select">
                <option value="">選択してください</option>
                <option v-for="c in classOptions" :key="c" :value="c">{{ c }}</option>
              </select>
            </div>
            <div class="form-group">
              <label class="form-label" for="message">メッセージ</label>
              <textarea
                id="message"
                v-model="form.message"
                class="form-input form-textarea"
                placeholder="ご質問・ご要望などお気軽にどうぞ"
                rows="4"
              ></textarea>
            </div>
            <button type="submit" class="btn btn--submit">
              <span v-if="!submitted">送信する</span>
              <span v-else>送信しました ✓</span>
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

const form = reactive({
  name: '',
  email: '',
  className: '',
  message: '',
})

const details = [
  { icon: '📍', label: '住所', value: '東京都渋谷区〇〇 1-2-3' },
  { icon: '📞', label: '電話', value: '03-XXXX-XXXX' },
  { icon: '🕐', label: '受付時間', value: '月〜土 10:00〜20:00' },
]

const classOptions = [
  '新体操ジュニア（基礎）',
  '新体操ジュニア（中級）',
  '競技クラス',
  'ボディメイキング',
  '大人の新体操',
  'その他・未定',
]

function handleSubmit() {
  submitted.value = true
  setTimeout(() => { submitted.value = false }, 3000)
  Object.assign(form, { name: '', email: '', className: '', message: '' })
}
</script>

<style scoped>
.contact {
  padding: var(--section-padding) 0;
  background: white;
}

.contact__inner {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 80px;
  align-items: start;
}

.section-label {
  font-family: var(--font-serif);
  font-size: 12px;
  font-weight: 300;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--pink-500);
  margin-bottom: 20px;
  display: block;
}

.section-title {
  font-family: var(--font-serif);
  font-size: clamp(26px, 3vw, 40px);
  font-weight: 300;
  letter-spacing: 0.02em;
  line-height: 1.4;
  color: var(--gray-900);
  margin-bottom: 24px;
}

.section-title em {
  font-style: italic;
  color: var(--pink-600);
}

.contact__text {
  font-size: 15px;
  line-height: 2;
  color: var(--gray-600);
  margin-bottom: 40px;
}

.contact__details {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.contact__detail {
  display: flex;
  align-items: flex-start;
  gap: 16px;
}

.contact__detail-icon {
  font-size: 18px;
  margin-top: 2px;
}

.contact__detail-label {
  display: block;
  font-size: 11px;
  letter-spacing: 0.1em;
  color: var(--gray-400);
  margin-bottom: 2px;
}

.contact__detail-value {
  font-size: 14px;
  font-weight: 500;
  color: var(--gray-800);
}

/* Form */
.contact__form-wrap {
  background: var(--pink-50);
  border-radius: 24px;
  padding: 48px;
  border: 1px solid var(--pink-100);
}

.contact__form {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.form-label {
  font-size: 13px;
  font-weight: 500;
  color: var(--gray-700, #404040);
  letter-spacing: 0.02em;
  display: flex;
  align-items: center;
  gap: 8px;
}

.form-required {
  font-size: 10px;
  font-weight: 600;
  background: var(--pink-500);
  color: white;
  padding: 2px 7px;
  border-radius: 4px;
  letter-spacing: 0.04em;
}

.form-input {
  width: 100%;
  padding: 14px 18px;
  font-size: 14px;
  font-family: var(--font-sans);
  color: var(--gray-800);
  background: white;
  border: 1.5px solid var(--pink-200);
  border-radius: 12px;
  outline: none;
  transition: border-color var(--transition-fast), box-shadow var(--transition-fast);
  appearance: none;
}

.form-input::placeholder {
  color: var(--gray-400);
}

.form-input:focus {
  border-color: var(--pink-400);
  box-shadow: 0 0 0 4px rgba(236, 72, 153, 0.08);
}

.form-select {
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='16' height='16' viewBox='0 0 24 24' fill='none' stroke='%23a3a3a3' stroke-width='2'%3E%3Cpath d='m6 9 6 6 6-6'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 14px center;
  padding-right: 44px;
  cursor: pointer;
}

.form-textarea {
  resize: vertical;
  min-height: 120px;
  line-height: 1.7;
}

.btn--submit {
  width: 100%;
  padding: 16px;
  background: linear-gradient(135deg, var(--pink-500), var(--pink-700));
  color: white;
  font-size: 15px;
  font-weight: 600;
  letter-spacing: 0.1em;
  border-radius: 12px;
  border: none;
  cursor: pointer;
  transition: all var(--transition-base);
  box-shadow: 0 6px 24px rgba(236, 72, 153, 0.3);
}

.btn--submit:hover {
  transform: translateY(-1px);
  box-shadow: 0 10px 32px rgba(236, 72, 153, 0.4);
}

.btn--submit:active {
  transform: translateY(0);
}

@media (max-width: 900px) {
  .contact__inner {
    grid-template-columns: 1fr;
    gap: 48px;
  }

  .contact__form-wrap {
    padding: 32px 24px;
  }
}
</style>
