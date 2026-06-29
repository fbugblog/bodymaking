<template>
  <section id="schedule" class="schedule">
    <div class="container">
      <div class="schedule__header">
        <p class="s-label reveal">Schedule</p>
        <h2 class="schedule__title reveal reveal-delay-1">週間スケジュール</h2>
        <p class="schedule__sub reveal reveal-delay-2">お好きな時間帯のクラスをお選びください。</p>
      </div>

      <div class="schedule__wrap reveal">
        <table class="sched-table">
          <thead>
            <tr>
              <th class="sched-table__th sched-table__th--time">時間</th>
              <th class="sched-table__th" v-for="d in days" :key="d">{{ d }}</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="row in rows" :key="row.time" class="sched-table__row">
              <td class="sched-table__td sched-table__td--time">{{ row.time }}</td>
              <td class="sched-table__td" v-for="d in days" :key="d">
                <div v-if="row.cells[d]" class="sched-cell" :class="`sched-cell--${row.cells[d].theme}`">
                  <span class="sched-cell__name">{{ row.cells[d].name }}</span>
                  <span class="sched-cell__age">{{ row.cells[d].age }}</span>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>

      <div class="schedule__legend reveal">
        <div class="legend-item" v-for="l in legend" :key="l.label">
          <span class="legend-dot" :class="`legend-dot--${l.theme}`"></span>
          <span>{{ l.label }}</span>
        </div>
      </div>

      <p class="schedule__note reveal">
        ※ スケジュールは変更になる場合があります。最新情報はお問い合わせください。
      </p>
    </div>
  </section>
</template>

<script setup>
const days = ['月','火','水','木','金','土','日']

const rows = [
  { time: '10:00〜11:00', cells: {
    '月': { name:'ボディメイキング', age:'大人', theme:'c' },
    '水': { name:'ボディメイキング', age:'大人', theme:'c' },
    '金': { name:'大人の新体操', age:'18歳〜', theme:'d' },
    '土': { name:'ジュニア基礎', age:'4〜7歳', theme:'a' },
    '日': { name:'ジュニア基礎', age:'4〜7歳', theme:'a' },
  }},
  { time: '14:00〜15:00', cells: {
    '水': { name:'ジュニア初級', age:'6〜12歳', theme:'a' },
    '木': { name:'ジュニア中級', age:'6〜15歳', theme:'a' },
    '土': { name:'ジュニア中級', age:'6〜15歳', theme:'a' },
    '日': { name:'大人の新体操', age:'18歳〜', theme:'d' },
  }},
  { time: '16:00〜17:30', cells: {
    '火': { name:'競技クラス', age:'6歳〜', theme:'b' },
    '木': { name:'競技クラス', age:'6歳〜', theme:'b' },
    '土': { name:'競技クラス', age:'6歳〜', theme:'b' },
  }},
  { time: '19:00〜20:00', cells: {
    '月': { name:'大人の新体操', age:'18歳〜', theme:'d' },
    '火': { name:'ボディメイキング', age:'大人', theme:'c' },
    '木': { name:'ボディメイキング', age:'大人', theme:'c' },
    '金': { name:'ボディメイキング', age:'大人', theme:'c' },
  }},
]

const legend = [
  { theme: 'a', label: '新体操ジュニア' },
  { theme: 'b', label: '競技クラス' },
  { theme: 'c', label: 'ボディメイキング' },
  { theme: 'd', label: '大人の新体操' },
]
</script>

<style scoped>
.schedule {
  padding: clamp(100px, 12vw, 160px) 0;
  background: var(--deep);
  position: relative;
}
.schedule::before {
  content: '';
  position: absolute;
  inset: 0;
  background: repeating-linear-gradient(
    -45deg,
    transparent,
    transparent 39px,
    rgba(255,255,255,0.008) 40px
  );
  pointer-events: none;
}

.schedule__header { margin-bottom: 56px; }
.schedule__title {
  font-family: var(--font-serif);
  font-size: clamp(28px, 3.5vw, 48px);
  font-weight: 300;
  margin-bottom: 14px;
}
.schedule__sub {
  font-size: 14px;
  color: rgba(255,255,255,0.4);
}

.schedule__wrap {
  overflow-x: auto;
  border: 1px solid rgba(255,255,255,0.06);
  border-radius: 20px;
  background: var(--surface);
}

.sched-table {
  width: 100%;
  border-collapse: collapse;
  min-width: 700px;
}

.sched-table__th {
  padding: 16px 12px;
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 0.12em;
  color: rgba(255,255,255,0.25);
  text-align: center;
  border-bottom: 1px solid rgba(255,255,255,0.05);
}
.sched-table__th--time {
  text-align: left;
  padding-left: 28px;
  min-width: 140px;
}

.sched-table__row:hover td { background: rgba(255,255,255,0.015); }
.sched-table__td {
  padding: 12px 8px;
  border-bottom: 1px solid rgba(255,255,255,0.04);
  text-align: center;
  vertical-align: middle;
  transition: background .2s;
}
.sched-table__td--time {
  text-align: left;
  padding-left: 28px;
  font-size: 12px;
  color: rgba(255,255,255,0.3);
  white-space: nowrap;
  font-weight: 500;
}
.sched-table__row:last-child td { border-bottom: none; }

.sched-cell {
  display: flex;
  flex-direction: column;
  gap: 2px;
  padding: 9px 12px;
  border-radius: 10px;
  align-items: center;
  border: 1px solid transparent;
  transition: transform .25s var(--ease-back);
}
.sched-cell:hover { transform: scale(1.03); }

.sched-cell--a { background: rgba(233,30,140,0.1); border-color: rgba(233,30,140,0.2); }
.sched-cell--b { background: rgba(201,169,110,0.1); border-color: rgba(201,169,110,0.2); }
.sched-cell--c { background: rgba(255,255,255,0.04); border-color: rgba(255,255,255,0.08); }
.sched-cell--d { background: rgba(255,107,193,0.08); border-color: rgba(255,107,193,0.15); }

.sched-cell__name {
  font-size: 11px;
  font-weight: 600;
  line-height: 1.3;
}
.sched-cell--a .sched-cell__name { color: var(--pink-light); }
.sched-cell--b .sched-cell__name { color: var(--gold-light); }
.sched-cell--c .sched-cell__name { color: rgba(255,255,255,0.7); }
.sched-cell--d .sched-cell__name { color: #FFB3DC; }

.sched-cell__age {
  font-size: 10px;
  color: rgba(255,255,255,0.3);
}

.schedule__legend {
  display: flex;
  gap: 28px;
  flex-wrap: wrap;
  margin-top: 24px;
}
.legend-item {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 12px;
  color: rgba(255,255,255,0.4);
}
.legend-dot {
  width: 8px; height: 8px;
  border-radius: 2px;
  flex-shrink: 0;
}
.legend-dot--a { background: var(--pink); }
.legend-dot--b { background: var(--gold); }
.legend-dot--c { background: rgba(255,255,255,0.3); }
.legend-dot--d { background: #FFB3DC; }

.schedule__note {
  margin-top: 20px;
  font-size: 11px;
  color: rgba(255,255,255,0.2);
}
</style>
