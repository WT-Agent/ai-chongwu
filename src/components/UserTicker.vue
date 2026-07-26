<template>
  <div class="glass-card ticker-card">
    <div class="ticker-wrapper">
      <div v-for="(item, index) in tickerItems" :key="index" class="ticker-item">
        <span>{{ item.text }}</span>
        <span style="color: var(--success-color); font-weight: bold;">[养护方案生成完成]</span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const tickerItems = ref([
  { text: '用户 138****9281 完成了 3 个月英短幼猫离乳过渡食谱与多吃肉泥配比' },
  { text: '用户 177****4019 完成了边牧犬分离焦虑乱吠叫的正向强化训练方案' },
  { text: '用户 189****3320 完成了老龄金毛犬关节保健与高蛋白软食护理指南' },
  { text: '用户 131****8829 解锁了猫咪乱发脾气乱拉乱尿行为心理诊断' },
  { text: '用户 153****1290 生成了夏季宠物中暑预防与急救居家观察要点' },
]);
</script>
