<template>
  <section class="nomads-showcase-section">
    <div class="showcase-header">
      <div class="header-left">
        <h2 class="showcase-title">宠物养护与健康照护实战模板库</h2>
        <p class="showcase-subtitle">精选科学喂养、行为矫正与老龄护理，点击“一键套用”生成专业方案</p>
      </div>
      <span class="showcase-badge">已收录 {{ showcaseItems.length }} 个养护指南模板</span>
    </div>

    <div class="showcase-grid">
      <div 
        v-for="item in showcaseItems" 
        :key="item.id" 
        class="glass-card showcase-card"
      >
        <div class="card-header">
          <span class="scenario-tag">{{ item.tag }}</span>
          <span class="usage-count">{{ item.usageCount }} 次生成</span>
        </div>

        <div class="card-content">
          <h3 class="item-title">{{ item.title }}</h3>
          <p class="item-prompt">“{{ item.prompt }}”</p>
        </div>

        <div class="card-action">
          <button class="apply-btn" @click="applyTemplate(item)">
            <span>一键套用</span>
            <svg class="arrow-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <line x1="5" y1="12" x2="19" y2="12"></line>
              <polyline points="12 5 19 12 12 19"></polyline>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const emit = defineEmits<{
  (e: 'apply-template', payload: { prompt: string; careType?: string; petType?: string }): void;
}>();

export interface ShowcaseItem {
  id: string;
  tag: string;
  title: string;
  prompt: string;
  careType?: string;
  petType?: string;
  usageCount: string;
}

const showcaseItems = computed<ShowcaseItem[]>(() => [
  {
    id: 'chongwu-1',
    tag: '幼宠食谱',
    title: '3个月幼猫离乳过渡食谱与发毛营养配比',
    prompt: '为 3 个月英短幼猫制定科学离乳食谱，包含幼猫粮泡软过渡、主罐湿粮补充、钙质与 DHA 营养配比及每日喂食频次。',
    careType: '科学喂养与食谱营养搭配',
    petType: '猫咪 (猫主子)',
    usageCount: '62.4k'
  },
  {
    id: 'chongwu-2',
    tag: '行为矫正',
    title: '狗狗独自在家分离焦虑与吠叫拆家训练',
    prompt: '边牧犬主人出门后频繁吠叫与撕咬沙发，提供正向强化响片训练、出游消耗体力及脱敏离家练习方案。',
    careType: '异常行为与心理矫正指南',
    petType: '狗狗 (汪星人)',
    usageCount: '55.1k'
  },
  {
    id: 'chongwu-3',
    tag: '老龄照护',
    title: '9岁老龄犬关节保健与易消化高蛋白饮食',
    prompt: '针对 9 岁老龄金毛犬关节硬化与行动变慢，定制软骨素补充方案、易消化湿粮蒸肉及防滑居家环境改造。',
    careType: '日常卫生洗护与健康护理',
    petType: '狗狗 (汪星人)',
    usageCount: '48.9k'
  },
  {
    id: 'chongwu-4',
    tag: '多猫应激',
    title: '多猫家庭原住猫与新猫接引应激排便矫正',
    prompt: '新猫到家后原住猫出现乱拉乱尿与躲藏行为，提供隔离分域、费洛蒙环境抚慰及同吃冻干建立正向联想步骤。',
    careType: '异常行为与心理矫正指南',
    petType: '猫咪 (猫主子)',
    usageCount: '41.3k'
  },
  {
    id: 'chongwu-5',
    tag: '急救预警',
    title: '狗狗误食巧克力/葡萄及夏季中暑急救',
    prompt: '梳理狗狗绝对禁忌食物清单，列出误食巧克力与葡萄的催吐急救判断红线，以及炎热天气中暑物理降温指南。',
    careType: '阶段疾病预警与急救常识',
    petType: '狗狗 (汪星人)',
    usageCount: '59.7k'
  },
  {
    id: 'chongwu-6',
    tag: '异宠养护',
    title: '侏儒兔/仓鼠肠胃停滞预警与高纤维食谱',
    prompt: '针对侏儒兔食欲减退与粪便变小，制定无限量提摩西草主食方案、化毛膏使用频次及肠胃停滞紧急就医标准。',
    careType: '科学喂养与食谱营养搭配',
    petType: '异宠 (兔子/仓鼠/鸟类)',
    usageCount: '34.2k'
  }
]);

function applyTemplate(item: ShowcaseItem) {
  emit('apply-template', {
    prompt: item.prompt,
    careType: item.careType,
    petType: item.petType
  });
}
</script>

<style scoped>
.nomads-showcase-section {
  margin-top: 2rem;
  width: 100%;
}

.showcase-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  margin-bottom: 1.25rem;
  padding-bottom: 0.75rem;
  border-bottom: 1px solid var(--card-border);
}

.showcase-title {
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--text-primary);
  background: var(--primary-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.showcase-subtitle {
  font-size: 0.825rem;
  color: var(--text-secondary);
  margin-top: 0.25rem;
}

.showcase-badge {
  font-size: 0.75rem;
  color: #a5b4fc;
  background: rgba(99, 102, 241, 0.12);
  border: 1px solid rgba(99, 102, 241, 0.25);
  padding: 4px 10px;
  border-radius: 20px;
}

.showcase-grid {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 1.25rem;
}

@media (min-width: 640px) {
  .showcase-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .showcase-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

.showcase-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  padding: 1.25rem;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid var(--card-border);
  border-radius: 14px;
  transition: all 0.25s ease;
}

.showcase-card:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(99, 102, 241, 0.4);
  transform: translateY(-3px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.75rem;
}

.scenario-tag {
  font-size: 0.75rem;
  font-weight: 600;
  padding: 3px 8px;
  border-radius: 6px;
  background: rgba(168, 85, 247, 0.15);
  color: #c084fc;
  border: 1px solid rgba(168, 85, 247, 0.3);
}

.usage-count {
  font-size: 0.75rem;
  color: var(--text-secondary);
}

.card-content {
  margin-bottom: 1rem;
  flex: 1;
}

.item-title {
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.4rem;
}

.item-prompt {
  font-size: 0.825rem;
  color: var(--text-secondary);
  line-height: 1.45;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  font-style: italic;
}

.card-action {
  padding-top: 0.75rem;
  border-top: 1px solid rgba(255, 255, 255, 0.04);
}

.apply-btn {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  padding: 0.5rem 1rem;
  background: rgba(99, 102, 241, 0.1);
  border: 1px solid rgba(99, 102, 241, 0.3);
  border-radius: 8px;
  color: #a5b4fc;
  font-size: 0.825rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
}

.showcase-card:hover .apply-btn {
  background: var(--primary-gradient);
  border-color: transparent;
  color: white;
}

.arrow-icon {
  width: 14px;
  height: 14px;
  transition: transform 0.2s ease;
}

.apply-btn:hover .arrow-icon {
  transform: translateX(3px);
}
</style>
