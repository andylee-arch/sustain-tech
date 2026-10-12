<template>
  <div class="page-wrap">
    <section class="section hero-subpage">
      <div class="container narrow-copy">
        <span class="eyebrow">服务项目</span>
        <h1>从兴趣到能力，从课程到成果</h1>
        <p>
          我们围绕孩子的年龄特点、学习阶段与成长目标，提供工程项目实训、科创竞赛辅导与个性化学习规划，帮助学生在真实任务中建立解决问题的能力和创新意识。
        </p>
      </div>
    </section>

    <section class="section">
      <div class="container service-overview-grid">
        <div class="overview-card" v-for="item in services" :key="item.title">
          <div class="icon-wrap">{{ item.icon }}</div>
          <h3>{{ item.title }}</h3>
          <p>{{ item.summary }}</p>
          <ul>
            <li v-for="detail in item.details" :key="detail">{{ detail }}</li>
          </ul>
          <router-link class="btn btn-primary btn-sm" to="/contact">立即咨询</router-link>
        </div>
      </div>
    </section>

    <section class="section section-alt">
      <div class="container process-wrap">
        <div class="section-heading">
          <span class="eyebrow">服务流程</span>
          <h2>科学、清晰、可持续的学习路径</h2>
        </div>

        <div class="process-grid">
          <div class="process-item" v-for="(step, index) in steps" :key="step.title">
            <span class="step-no">0{{ index + 1 }}</span>
            <h3>{{ step.title }}</h3>
            <p>{{ step.text }}</p>
          </div>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="container cta-panel">
        <div>
          <span class="eyebrow">预约课程咨询</span>
          <h2>让孩子从好奇走向主动，从参与走向创造</h2>
        </div>
        <router-link class="btn btn-primary btn-lg" to="/contact">预约课程咨询</router-link>
      </div>
    </section>
  </div>
</template>

<script setup>
const services = [
  {
    icon: '⚙️',
    title: '工程项目实训',
    summary: '围绕真实工程任务培养学生的工程思维、设计能力和协作意识，让学习建立在“做中理解”的基础上。',
    details: ['适合年龄：小学至高中', '典型项目：智能小车、机器人搭建、编程挑战', '学习成果：跨学科能力提升、项目执行与表达训练']
  },
  {
    icon: '🏆',
    title: '科创竞赛辅导',
    summary: '结合当前竞赛趋势和项目要求，帮助孩子在选题、实施和展现中获得更有针对性的支持。',
    details: ['赛事方向：科技创新、编程与创客类赛事', '辅导内容：选题、计划、原型、演示与汇报训练', '成果支持：作品优化与赛前复盘']
  },
  {
    icon: '📘',
    title: '个性化学习规划',
    summary: '根据孩子的兴趣、能力差异和学习阶段，制定更适合其节奏的成长路径与课程安排。',
    details: ['评估维度：兴趣、基础、目标和学习习惯', '输出成果：学习路径、成长里程碑', '跟踪方式：阶段反馈与持续调整']
  }
]

const steps = [
  {
    title: '咨询与需求沟通',
    text: '家长与我们一起了解孩子的年龄、兴趣、现状与目标，明确最关注的成长方向。'
  },
  {
    title: '能力评估与定位',
    text: '结合孩子的学习阶段和基础情况，评估优势、短板和适合的课程方向。'
  },
  {
    title: '定制学习方案',
    text: '根据个体差异设计课程内容、节奏与成长目标，让学习更具针对性和可执行性。'
  },
  {
    title: '项目授课与跟踪',
    text: '在教学过程中持续跟踪表现并提供反馈，帮助孩子稳步建立信心、技能与方法。'
  }
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

.service-overview-grid {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1.5rem;
  padding: 0 1.2rem;
}

.overview-card {
  background: white;
  border: 1px solid #edf2f7;
  border-radius: 24px;
  padding: 2rem 1.5rem;
  box-shadow: 0 10px 24px rgba(15, 23, 42, 0.04);
}

.overview-card ul {
  list-style: none;
  margin: 1rem 0 1.5rem;
  display: grid;
  gap: 0.6rem;
  color: #4b5563;
}

.overview-card li::before {
  content: '•';
  color: #0052cc;
  margin-right: 0.6rem;
}

.process-wrap {
  max-width: 1200px;
  margin: 0 auto;
}

.process-grid {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 1.2rem;
}

.process-item {
  background: white;
  border: 1px solid #edf2f7;
  border-radius: 20px;
  padding: 1.5rem 1.2rem;
}

.step-no {
  display: inline-block;
  font-size: 1.3rem;
  color: #0052cc;
  font-weight: 700;
  margin-bottom: 0.75rem;
}

.cta-panel {
  max-width: 1200px;
  margin: 0 auto;
  background: linear-gradient(135deg, #0d1b2a, #0f3d7a);
  border-radius: 28px;
  padding: 2rem 1.5rem;
  color: white;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
}

.cta-panel h2 {
  color: white;
  max-width: 600px;
}

@media (max-width: 900px) {
  .service-overview-grid,
  .process-grid {
    grid-template-columns: 1fr 1fr;
  }
}

@media (max-width: 640px) {
  .service-overview-grid,
  .process-grid {
    grid-template-columns: 1fr;
  }

  .cta-panel {
    flex-direction: column;
    align-items: flex-start;
  }
}
</style>
