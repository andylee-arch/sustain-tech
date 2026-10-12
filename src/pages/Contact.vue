<template>
  <div class="page-wrap">
    <section class="section hero-subpage">
      <div class="container narrow-copy">
        <span class="eyebrow">学员案例</span>
        <h1>真实成长故事，帮助家长看见学习成效</h1>
        <p>
          我们通过项目作品、竞赛成果与能力提升过程，展示孩子在STEAM学习中的变化与突破，让家长更加清晰地理解教学价值与成长路径。
        </p>
      </div>
    </section>

    <section class="section">
      <div class="container">
        <div class="filter-bar">
          <button
            v-for="filter in filters"
            :key="filter"
            :class="['filter-btn', { active: activeFilter === filter }]"
            @click="activeFilter = filter"
          >
            {{ filter }}
          </button>
        </div>

        <div class="case-grid">
          <article v-for="item in filteredCases" :key="item.title" class="story-card">
            <div class="story-image" :style="{ background: item.image }"></div>
            <div class="story-body">
              <span class="case-tag">{{ item.category }}</span>
              <h3>{{ item.title }}</h3>
              <p class="meta">{{ item.grade }} · {{ item.project }}</p>
              <p>{{ item.summary }}</p>
              <button class="text-link" @click="selectedCase = item">查看详情</button>
            </div>
          </article>
        </div>
      </div>
    </section>

    <section class="section section-alt">
      <div class="container metrics-row">
        <div class="metric-box" v-for="metric in resultMetrics" :key="metric.label">
          <strong>{{ metric.value }}</strong>
          <span>{{ metric.label }}</span>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="container cta-panel">
        <div>
          <span class="eyebrow">案例共鸣</span>
          <h2>让您的孩子也成为下一个优秀案例</h2>
        </div>
        <router-link class="btn btn-primary btn-lg" to="/contact">立即咨询</router-link>
      </div>
    </section>

    <div v-if="selectedCase" class="modal-overlay" @click.self="selectedCase = null">
      <div class="modal-card">
        <button class="close-btn" @click="selectedCase = null">×</button>
        <span class="case-tag">{{ selectedCase.category }}</span>
        <h3>{{ selectedCase.title }}</h3>
        <p class="meta">{{ selectedCase.grade }} · {{ selectedCase.project }}</p>
        <div class="modal-story">
          <p><strong>项目背景：</strong>{{ selectedCase.background }}</p>
          <p><strong>学习过程：</strong>{{ selectedCase.process }}</p>
          <p><strong>最终成果：</strong>{{ selectedCase.result }}</p>
          <p><strong>家长感悟：</strong>{{ selectedCase.feedback }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed, ref } from 'vue'

const cases = [
  {
    title: '智能小车创新挑战',
    category: '项目作品',
    grade: '小学六年级',
    project: '智能小车路径规划',
    summary: '通过搭建与调试，孩子从陌生的电子元件到完整作品实现，逐步建立工程思维与协作能力。',
    background: '在课程中，学生需要完成小车结构搭建、传感器调试和路径规划任务，综合运用科学与技术知识。',
    process: '孩子在项目中逐步学习传感器识别、运动控制和迭代优化，学会从问题中拆解需求再逐步验证方案。',
    result: '团队作品在校内科技节中获得“最佳创意奖”，家长反馈孩子的自主学习和问题解决能力明显提升。',
    feedback: '“孩子不再只会做题，而是愿意主动尝试解决现实中的问题，这种转变非常明显。”',
    image: 'linear-gradient(135deg, #edf6ff, #dbeeff)'
  },
  {
    title: 'AI创意设计作品',
    category: '竞赛获奖',
    grade: '初中二年级',
    project: 'AI感知与交互设计',
    summary: '利用创意设计与编程知识完成智能交互方案，提升孩子在项目表达中的逻辑与创新能力。',
    background: '课程围绕智能识别与交互体验展开，结合现实场景设计作品方案，推动学生实践运用技术思维。',
    process: '学生在导师指导下完成需求分析、功能拆解、原型构建以及作品展示训练，逐步形成完整表达能力。',
    result: '作品在区域科技创新赛中获得优胜奖，孩子对学习主动性与创造力形成明显提升。',
    feedback: '“以前更注重结果，现在他会先思考为什么、怎么做，这种变化让我们特别欣喜。”',
    image: 'linear-gradient(135deg, #eafaf4, #d6f5ea)'
  },
  {
    title: 'STEAM综合能力提升',
    category: '能力提升',
    grade: '高中一年级',
    project: '项目思维训练',
    summary: '从基础思维训练到问题拆分和方案落地，帮助学生建立更成熟的学习方法与解决问题能力。',
    background: '面向学生在学科整合和项目表达上的痛点进行系统训练。',
    process: '老师通过任务拆解、阶段反馈和迭代训练，帮助学生从“被动完成任务”转向“主动规划与调整”。',
    result: '学生在学术项目和课程作业中的表达与结构化思维能力明显提升。',
    feedback: '“看到孩子在表达和方案设计上的变化，家庭和老师都认可他已经具备更强的学习底盘。”',
    image: 'linear-gradient(135deg, #fff5e7, #ffe3ba)'
  }
]

const filters = ['全部', '项目作品', '竞赛获奖', '能力提升']
const activeFilter = ref('全部')

const filteredCases = computed(() => {
  if (activeFilter.value === '全部') return cases
  return cases.filter((item) => item.category === activeFilter.value)
})

const selectedCase = ref(null)

const resultMetrics = [
  { value: '500+', label: '累计服务学员' },
  { value: '100+', label: '学员获奖数' },
  { value: '20+', label: '项目课程' },
  { value: '98%', label: '家长满意度' }
]
</script>

<style scoped>
.hero-subpage {
  background: linear-gradient(180deg, #f3f8ff 0%, #ffffff 100%);
}

.narrow-copy {
  max-width: 900px;
  margin: 0 auto;
  text-align: center;
  padding: 1.5rem 1.2rem 0;
}

.filter-bar {
  max-width: 1200px;
  margin: 0 auto 2rem;
  padding: 0 1.2rem;
  display: flex;
  flex-wrap: wrap;
  gap: 0.8rem;
}

.filter-btn {
  padding: 0.7rem 1rem;
  border: 1px solid #dfeaf8;
  background: white;
  border-radius: 999px;
  font-weight: 600;
  color: #48576c;
  cursor: pointer;
}

.filter-btn.active {
  background: #0052cc;
  color: white;
  border-color: #0052cc;
}

.case-grid {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1.5rem;
  padding: 0 1.2rem;
}

.story-card {
  background: white;
  border: 1px solid #edf2f7;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 10px 22px rgba(15, 23, 42, 0.04);
}

.story-image {
  height: 200px;
}

.story-body {
  padding: 1.4rem;
}

.meta {
  color: #637088;
  font-size: 0.9rem;
  margin-bottom: 0.8rem;
}

.text-link {
  margin-top: 0.8rem;
  background: transparent;
  border: none;
  color: #0052cc;
  font-weight: 700;
  cursor: pointer;
}

.metrics-row {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 1rem;
  padding: 0 1.2rem;
}

.metric-box {
  background: white;
  border: 1px solid #edf2f7;
  border-radius: 18px;
  padding: 2rem 1rem;
  text-align: center;
}

.metric-box strong {
  display: block;
  color: #0052cc;
  font-size: 2rem;
  margin-bottom: 0.4rem;
}

.modal-overlay {
  position: fixed;
  inset: 0;
  background: rgba(15, 23, 42, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1rem;
  z-index: 2000;
}

.modal-card {
  position: relative;
  width: min(720px, 100%);
  background: white;
  border-radius: 24px;
  padding: 2rem;
  box-shadow: 0 30px 60px rgba(15, 23, 42, 0.2);
}

.close-btn {
  position: absolute;
  right: 1rem;
  top: 1rem;
  width: 36px;
  height: 36px;
  border-radius: 50%;
  border: 1px solid #dfeaf8;
  background: white;
  cursor: pointer;
  color: #1f2937;
  font-size: 1.3rem;
}

.modal-story {
  margin-top: 1rem;
  display: grid;
  gap: 0.8rem;
  color: #495057;
}

@media (max-width: 900px) {
  .case-grid,
  .metrics-row {
    grid-template-columns: 1fr 1fr;
  }
}

@media (max-width: 620px) {
  .case-grid,
  .metrics-row {
    grid-template-columns: 1fr;
  }
}
</style>
