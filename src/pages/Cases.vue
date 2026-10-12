<template>
  <div class="page-wrap">
    <section class="section hero-subpage">
      <div class="container narrow-copy">
        <span class="eyebrow">师资团队</span>
        <h1>工程背景与教育经验并重的导师团队</h1>
        <p>
          我们秉持“用真实项目培养真实能力”的教学理念，选拔具备工程实践、教育表达和学习辅导经验的导师，帮助孩子在学习中建立信心与方法。
        </p>
      </div>
    </section>

    <section class="section">
      <div class="container team-grid">
        <article class="mentor-card" v-for="mentor in mentors" :key="mentor.name">
          <div class="mentor-avatar">{{ mentor.initials }}</div>
          <div class="mentor-top">
            <h3>{{ mentor.name }}</h3>
            <span>{{ mentor.title }}</span>
          </div>
          <p class="mentor-quote">{{ mentor.philosophy }}</p>
          <ul>
            <li><strong>专业背景：</strong>{{ mentor.background }}</li>
            <li><strong>擅长领域：</strong>{{ mentor.specialty }}</li>
            <li><strong>教学年限：</strong>{{ mentor.experience }}</li>
          </ul>
        </article>
      </div>
    </section>

    <section class="section section-alt">
      <div class="container">
        <div class="section-heading">
          <span class="eyebrow">团队资质</span>
          <h2>专业、稳定、可持续的教学支撑</h2>
        </div>

        <div class="cert-grid">
          <div class="cert-item" v-for="cert in credentials" :key="cert.title">
            <div class="cert-icon">{{ cert.icon }}</div>
            <h3>{{ cert.title }}</h3>
            <p>{{ cert.text }}</p>
          </div>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="container cta-panel dark-panel">
        <div>
          <span class="eyebrow light">预约导师沟通</span>
          <h2>了解孩子适合哪种学习路径</h2>
        </div>
        <router-link class="btn btn-primary btn-lg" to="/contact">预约导师沟通</router-link>
      </div>
    </section>
  </div>
</template>

<script setup>
const mentors = [
  {
    name: '程老师',
    initials: '程',
    title: 'STEM课程总监',
    philosophy: '让孩子在真实工程任务中建立信心与方法，让学习从“被动听讲”转向“主动构建”。',
    background: '机械工程 + 教育研究',
    specialty: '机器人设计、项目式教学、课程研发',
    experience: '8年教育与教学实践'
  },
  {
    name: '陆老师',
    initials: '陆',
    title: '创客项目导师',
    philosophy: '以任务驱动的方式帮助孩子理解科学原理与工程逻辑，提升综合解决问题的能力。',
    background: '计算机科学与智能交互',
    specialty: '编程教学、创意设计、作品规划',
    experience: '6年项目辅导经验'
  },
  {
    name: '林老师',
    initials: '林',
    title: '教学研发顾问',
    philosophy: '把复杂知识拆解成可执行步骤，让每个孩子都能看到自己成长的路径。',
    background: '教育学与学习科学',
    specialty: '学习规划、能力评估、学情跟踪',
    experience: '7年学科辅导经验'
  },
  {
    name: '周老师',
    initials: '周',
    title: '竞赛辅导导师',
    philosophy: '帮助孩子在作品设计、表达沟通与赛前准备中形成完整的竞争力。',
    background: '设计与创新实践',
    specialty: '科技竞赛、汇报训练、作品优化',
    experience: '5年竞赛辅导经验'
  }
]

const credentials = [
  {
    icon: '🏅',
    title: '双师型教学标准',
    text: '导师团队兼具工程经验与教育教学背景，确保课程更贴近孩子真实学习需求。'
  },
  {
    icon: '📚',
    title: '项目化课程设计',
    text: '课程不只是知识传递，而是通过真实任务和阶段反馈来帮助孩子形成能力。'
  },
  {
    icon: '📈',
    title: '持续成长反馈',
    text: '通过过程记录和反馈机制，让家长清晰看到孩子的学习改变与成长方向。'
  }
]
</script>

<style scoped>
.hero-subpage {
  background: linear-gradient(180deg, #f5f9ff 0%, #ffffff 100%);
}

.narrow-copy {
  max-width: 900px;
  margin: 0 auto;
  text-align: center;
  padding: 1.5rem 1.2rem 0;
}

.team-grid {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 1.5rem;
  padding: 0 1.2rem;
}

.mentor-card {
  background: white;
  border: 1px solid #edf2f7;
  border-radius: 22px;
  padding: 1.6rem;
  box-shadow: 0 10px 22px rgba(15, 23, 42, 0.03);
}

.mentor-avatar {
  width: 64px;
  height: 64px;
  border-radius: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #0052cc, #00a3e0);
  color: white;
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
}

.mentor-top {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 0.8rem;
  flex-wrap: wrap;
  margin-bottom: 0.8rem;
}

.mentor-top h3 {
  margin: 0;
}

.mentor-top span {
  background: rgba(0, 82, 204, 0.08);
  color: #0052cc;
  border-radius: 999px;
  padding: 0.4rem 0.7rem;
  font-size: 0.75rem;
  font-weight: 700;
}

.mentor-quote {
  color: #495057;
  margin-bottom: 1rem;
}

.mentor-card ul {
  list-style: none;
  display: grid;
  gap: 0.7rem;
  color: #4b5563;
}

.cert-grid {
  max-width: 1100px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1.3rem;
  padding: 0 1.2rem;
}

.cert-item {
  background: white;
  border: 1px solid #edf2f7;
  border-radius: 20px;
  padding: 1.5rem;
}

.cert-icon {
  width: 56px;
  height: 56px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border-radius: 16px;
  background: linear-gradient(135deg, #edf6ff, #e0f5ff);
  font-size: 1.8rem;
  margin-bottom: 1rem;
}

.dark-panel {
  background: linear-gradient(135deg, #11243f, #163e75);
  color: white;
}

.light {
  background: rgba(255, 255, 255, 0.12);
  color: white;
}

.dark-panel h2 {
  color: white;
}

@media (max-width: 760px) {
  .team-grid,
  .cert-grid {
    grid-template-columns: 1fr;
  }
}
</style>
