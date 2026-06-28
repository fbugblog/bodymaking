<template>
  <section id="schedule" class="schedule">
    <div class="container">
      <div class="schedule__header">
        <p class="section-label">Schedule</p>
        <h2 class="section-title">スケジュール</h2>
        <p class="schedule__subtitle">お好きな時間帯のクラスをお選びください。</p>
      </div>

      <div class="schedule__table-wrap">
        <table class="schedule__table">
          <thead>
            <tr>
              <th class="schedule__th schedule__th--time">時間</th>
              <th class="schedule__th" v-for="day in days" :key="day">{{ day }}</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="row in schedule" :key="row.time">
              <td class="schedule__td schedule__td--time">{{ row.time }}</td>
              <td
                class="schedule__td"
                v-for="day in days"
                :key="day"
              >
                <div
                  v-if="row.cells[day]"
                  class="schedule__cell"
                  :class="`schedule__cell--${row.cells[day].color}`"
                >
                  <span class="schedule__cell-name">{{ row.cells[day].name }}</span>
                  <span class="schedule__cell-age">{{ row.cells[day].age }}</span>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>

      <div class="schedule__legend">
        <div class="schedule__legend-item" v-for="l in legend" :key="l.label">
          <span class="schedule__legend-dot" :class="`schedule__legend-dot--${l.color}`"></span>
          <span>{{ l.label }}</span>
        </div>
      </div>

      <p class="schedule__note">
        ※ スケジュールは変更になる場合があります。最新情報はお問い合わせください。
      </p>
    </div>
  </section>
</template>

<script setup>
const days = ['月', '火', '水', '木', '金', '土', '日']

const schedule = [
  {
    time: '10:00〜11:00',
    cells: {
      '月': { name: 'ボディメイキング', age: '大人', color: 'dark' },
      '水': { name: 'ボディメイキング', age: '大人', color: 'dark' },
      '金': { name: '大人の新体操', age: '18歳〜', color: 'light' },
      '土': { name: 'ジュニア基礎', age: '4〜7歳', color: 'pink' },
      '日': { name: 'ジュニア基礎', age: '4〜7歳', color: 'pink' },
    },
  },
  {
    time: '14:00〜15:00',
    cells: {
      '水': { name: 'ジュニア初級', age: '6〜12歳', color: 'pink' },
      '木': { name: 'ジュニア中級', age: '6〜15歳', color: 'pink' },
      '土': { name: 'ジュニア中級', age: '6〜15歳', color: 'pink' },
      '日': { name: '大人の新体操', age: '18歳〜', color: 'light' },
    },
  },
  {
    time: '16:00〜17:30',
    cells: {
      '火': { name: '競技クラス', age: '6歳〜', color: 'gold' },
      '木': { name: '競技クラス', age: '6歳〜', color: 'gold' },
      '土': { name: '競技クラス', age: '6歳〜', color: 'gold' },
    },
  },
  {
    time: '19:00〜20:00',
    cells: {
      '月': { name: '大人の新体操', age: '18歳〜', color: 'light' },
      '火': { name: 'ボディメイキング', age: '大人', color: 'dark' },
      '木': { name: 'ボディメイキング', age: '大人', color: 'dark' },
      '金': { name: 'ボディメイキング', age: '大人', color: 'dark' },
    },
  },
]

const legend = [
  { color: 'pink', label: '新体操ジュニア' },
  { color: 'gold', label: '競技クラス' },
  { color: 'dark', label: 'ボディメイキング' },
  { color: 'light', label: '大人の新体操' },
]
</script>

<style scoped>
.schedule {
  padding: var(--section-padding) 0;
  background: var(--pink-50);
}

.schedule__header {
  text-align: center;
  margin-bottom: 56px;
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

.schedule__subtitle {
  font-size: 15px;
  color: var(--gray-500, #737373);
}

.schedule__table-wrap {
  overflow-x: auto;
  border-radius: 20px;
  box-shadow: 0 4px 24px rgba(0,0,0,0.06);
  background: white;
}

.schedule__table {
  width: 100%;
  border-collapse: collapse;
  min-width: 700px;
}

.schedule__th {
  padding: 16px 12px;
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 0.1em;
  color: var(--gray-500, #737373);
  text-align: center;
  background: white;
  border-bottom: 1px solid var(--gray-100);
}

.schedule__th--time {
  text-align: left;
  padding-left: 24px;
  min-width: 130px;
}

.schedule__td {
  padding: 12px 8px;
  border-bottom: 1px solid var(--gray-100);
  vertical-align: middle;
  text-align: center;
}

.schedule__td--time {
  font-size: 12px;
  font-weight: 500;
  color: var(--gray-600);
  text-align: left;
  padding-left: 24px;
  white-space: nowrap;
}

.schedule__cell {
  display: flex;
  flex-direction: column;
  gap: 2px;
  padding: 8px 10px;
  border-radius: 10px;
  align-items: center;
}

.schedule__cell--pink {
  background: var(--pink-50);
  border: 1px solid var(--pink-200);
}

.schedule__cell--gold {
  background: var(--gold-100);
  border: 1px solid var(--gold-200);
}

.schedule__cell--dark {
  background: #1a0a12;
  border: 1px solid rgba(255,255,255,0.05);
}

.schedule__cell--light {
  background: var(--pink-100);
  border: 1px solid var(--pink-200);
}

.schedule__cell-name {
  font-size: 11px;
  font-weight: 600;
  line-height: 1.3;
}

.schedule__cell--pink .schedule__cell-name { color: var(--pink-700); }
.schedule__cell--gold .schedule__cell-name { color: var(--gold-600); }
.schedule__cell--dark .schedule__cell-name { color: rgba(255,255,255,0.85); }
.schedule__cell--light .schedule__cell-name { color: var(--pink-800); }

.schedule__cell-age {
  font-size: 10px;
  opacity: 0.6;
  color: inherit;
}

.schedule__cell--dark .schedule__cell-age { color: rgba(255,255,255,0.5); }

.schedule__legend {
  display: flex;
  gap: 28px;
  justify-content: center;
  flex-wrap: wrap;
  margin-top: 28px;
}

.schedule__legend-item {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 12px;
  color: var(--gray-600);
}

.schedule__legend-dot {
  width: 10px;
  height: 10px;
  border-radius: 3px;
  flex-shrink: 0;
}

.schedule__legend-dot--pink { background: var(--pink-400); }
.schedule__legend-dot--gold { background: var(--gold-400); }
.schedule__legend-dot--dark { background: #3d1230; }
.schedule__legend-dot--light { background: var(--pink-300); }

.schedule__note {
  text-align: center;
  font-size: 12px;
  color: var(--gray-400);
  margin-top: 20px;
}
</style>
