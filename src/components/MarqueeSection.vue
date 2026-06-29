<template>
  <div class="marquee-wrap">
    <div class="marquee">
      <div class="marquee__track">
        <span v-for="n in 8" :key="'a'+n" class="marquee__item">
          Body Making <em>✦</em> 新体操 <span class="marquee__sep">◆</span>
          Rhythmic Gymnastics <em>✦</em> Studio Grace <span class="marquee__sep">◆</span>
        </span>
      </div>
    </div>
    <div class="marquee" style="margin-top:-1px;">
      <div class="marquee__track marquee__track--reverse">
        <span v-for="n in 8" :key="'b'+n" class="marquee__item marquee__item--gold">
          Elegant <em>✦</em> Graceful <span class="marquee__sep">◆</span>
          Beautiful <em>✦</em> Powerful <span class="marquee__sep">◆</span>
        </span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.marquee-wrap {
  padding: 0;
  overflow: hidden;
  border-top: 1px solid rgba(255,255,255,0.04);
  border-bottom: 1px solid rgba(255,255,255,0.04);
  background: rgba(255,255,255,0.015);
}
.marquee__item em {
  font-style: italic;
  color: rgba(233,30,140,0.4);
  font-family: var(--font-serif);
}
.marquee__item--gold em { color: rgba(201,169,110,0.4); }
</style>
