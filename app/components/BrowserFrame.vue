<script setup>
import { computed } from 'vue'

const props = defineProps({
  url: { type: String, default: 'trait-compass.trait-compass.workers.dev' },
  caption: { type: String, default: '' },
  src: { type: String, default: '' },
  alt: { type: String, default: '' },
  height: { type: String, default: '190px' },
  objectFit: { type: String, default: 'cover' },
  objectPosition: { type: String, default: 'center' },
})

const resolvedSrc = computed(() =>
  props.src ? `${import.meta.env.BASE_URL}${props.src.replace(/^\//, '')}` : ''
)
</script>

<template>
  <figure class="browser-frame">
    <div class="chrome">
      <span class="dot" /><span class="dot" /><span class="dot" />
      <div class="address-bar">{{ url }}</div>
    </div>
    <div class="viewport" :style="{ height }">
      <img
        v-if="resolvedSrc"
        :src="resolvedSrc"
        :alt="alt || caption"
        :style="{ objectFit, objectPosition }"
      />
      <div v-else class="placeholder">
        <div class="placeholder-title">スクリーンショット未挿入</div>
        <div class="placeholder-hint">public/images/README.md の手順で撮影した1600×900pxの画像を<br />images/ に追加し、src で参照してください</div>
      </div>
    </div>
    <figcaption v-if="caption">{{ caption }}</figcaption>
  </figure>
</template>

<style scoped>
.browser-frame {
  margin: 0;
  border: 1px solid var(--tc-border);
  border-radius: 8px;
  overflow: hidden;
  background: #fff;
  box-shadow: 0 1px 3px rgba(22, 35, 63, 0.08);
}

.chrome {
  display: flex;
  align-items: center;
  gap: 6px;
  background: #eef0f3;
  padding: 8px 12px;
  border-bottom: 1px solid var(--tc-border);
}

.dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #c7cbd1;
}

.address-bar {
  margin-left: 10px;
  flex: 1;
  background: #ffffff;
  border: 1px solid var(--tc-border);
  border-radius: 999px;
  padding: 3px 14px;
  font-size: 12px;
  color: var(--tc-text-muted);
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.viewport {
  background: #f4f5f7;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.viewport img {
  width: 100%;
  height: 100%;
  display: block;
}

.placeholder {
  text-align: center;
  color: var(--tc-text-muted);
  padding: 16px;
}

.placeholder-title {
  font-size: 14px;
  font-weight: 700;
  margin-bottom: 8px;
}

.placeholder-hint {
  font-size: 11px;
  line-height: 1.6;
}

figcaption {
  padding: 8px 12px;
  font-size: 13px;
  color: var(--tc-text-muted);
  border-top: 1px solid var(--tc-border);
  background: #fafbfc;
}
</style>
