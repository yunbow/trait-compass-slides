<script setup>
defineProps({
  value: { type: String, required: true },
  valueSub: { type: String, default: '' },
  label: { type: String, required: true },
  source: { type: String, default: '' },
})
</script>

<template>
  <div class="metric-card">
    <div class="metric-value">
      {{ value }}<span v-if="valueSub" class="metric-value-sub">{{ valueSub }}</span>
    </div>
    <div class="metric-label">{{ label }}</div>
    <div v-if="source" class="metric-source">出典: {{ source }}</div>
  </div>
</template>

<style scoped>
.metric-card {
  flex: 1;
  display: flex;
  flex-direction: column;
  border-left: 4px solid var(--tc-green);
  background: #fafbfc;
  padding: 28px 32px;
  min-height: 220px;
}

.metric-value {
  font-size: 72px;
  font-weight: 900;
  color: var(--tc-navy);
  line-height: 1.1;
  white-space: nowrap;
}

.metric-value-sub {
  font-size: 24px;
  font-weight: 700;
  color: var(--tc-navy-soft);
  margin-left: 10px;
}

.metric-label {
  margin-top: 14px;
  font-size: 16px;
  color: var(--tc-text);
  line-height: 1.7;
}

.metric-source {
  margin-top: auto;
  padding-top: 14px;
  font-size: 16px;
  color: var(--tc-text-muted);
}
</style>
