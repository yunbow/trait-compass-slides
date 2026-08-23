<script setup>
// steps: [{ text: '箱の中身', note: '次の箱へ進む矢印に添える説明（省略可）' }]
defineProps({
  steps: { type: Array, required: true },
  direction: { type: String, default: 'vertical' }, // 'vertical' | 'horizontal'
})
</script>

<template>
  <div class="data-flow" :class="direction">
    <template v-for="(step, i) in steps" :key="i">
      <div class="flow-box">{{ step.text }}</div>
      <div v-if="i < steps.length - 1" class="flow-arrow">
        <div class="arrow-glyph">{{ direction === 'horizontal' ? '→' : '↓' }}</div>
        <div v-if="step.note" class="arrow-note">{{ step.note }}</div>
      </div>
    </template>
  </div>
</template>

<style scoped>
.data-flow {
  display: flex;
  width: 100%;
}

.data-flow.vertical {
  flex-direction: column;
  align-items: stretch;
}

.data-flow.horizontal {
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
}

.flow-box {
  background: var(--tc-navy);
  color: #ffffff;
  font-weight: 700;
  font-size: 16px;
  line-height: 1.6;
  text-align: center;
  padding: 16px 20px;
  border-radius: 4px;
  white-space: pre-line;
}

.data-flow.horizontal .flow-box {
  flex: 1;
  background: var(--tc-green);
}

.flow-arrow {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 6px 0;
}

.data-flow.vertical .flow-arrow {
  flex-direction: row;
  padding-left: 6px;
}

.data-flow.horizontal .flow-arrow {
  flex-direction: column;
  padding: 0 8px;
  flex: 0 0 auto;
}

.arrow-glyph {
  color: var(--tc-green);
  font-size: 24px;
  font-weight: 900;
  line-height: 1;
}

.arrow-note {
  font-size: 13px;
  color: var(--tc-text-muted);
  line-height: 1.5;
}
</style>
