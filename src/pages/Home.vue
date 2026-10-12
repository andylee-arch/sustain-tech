<template>
  <section class="hero-section section">
    <div class="container hero-layout">
      <div class="hero-copy">
        <span class="eyebrow">工程思维 · 项目实战 · 真实成长</span>
        <h1>让工程思维成为孩子的核心竞争力</h1>
        <p class="lead">
          专注K12 STEM项目式学习，以真实工程项目培养跨学科解决问题的能力。
        </p>

        <div class="hero-actions">
          <router-link class="btn btn-primary btn-lg" to="/contact">预约免费试听</router-link>
          <router-link class="btn btn-outline btn-lg" to="/services">了解课程</router-link>
        </div>

        <div class="hero-trust">
          <span>正规企业资质</span>
          <span>双师型教学</span>
          <span>家长口碑</span>
        </div>
      </div>

      <div class="hero-visual">
        <div class="feature-card card-main">
          <div class="mini-badge">项目式学习</div>
          <h3>从“做中学”到“会思考”</h3>
          <ul>
            <li>智能小车与机器人搭建</li>
            <li>编程与创意设计挑战</li>
            <li>真实工程任务导向训练</li>
          </ul>
        </div>
        <div class="feature-card card-float card-top">
          <strong>500+</strong>
          <span>累计服务学员</span>
        </div>
        <div class="feature-card card-float card-bottom">
          <strong>98%</strong>
          <span>家长满意度</span>
        </div>
      </div>
    </div>
  </section>

  <section class="section metrics-section">
    <div class="container grid grid-4 metrics-grid">
      <div class="metric-item">
        <strong>500+</strong>
        <span>累计服务学员</span>
      </div>
      <div class="metric-item">
        <strong>20+</strong>
        <span>项目课程</span>
      </div>
      <div class="metric-item">
        <strong>100+</strong>
        <span>学员参赛获奖</span>
      </div>
      <div class="metric-item">
        <strong>98%</strong>
        <span>家长满意度</span>
      </div>
    </div>
  </section>

  <section class="section services-overview">
    <div class="container">
      <div class="section-heading">
        <span class="eyebrow">核心服务</span>
        <h2>围绕孩子成长的三大能力路径</h2>
      </div>

      <div class="grid grid-3">
        <div class="service-card" v-for="service in services" :key="service.title">
          <div class="icon-wrap">{{ service.icon }}</div>
          <h3>{{ service.title }}</h3>
          <p>{{ service.description }}</p>
          <router-link :to="service.link">了解详情</router-link>
        </div>
      </div>
    </div>
  </section>

  <section class="section section-alt">
    <div class="container">
      <div class="section-heading">
        <span class="eyebrow">精选案例</span>
        <h2>真实成果，建立信任</h2>
      </div>

      <div class="grid grid-3 cases-grid">
        <article class="case-card" v-for="caseItem in cases" :key="caseItem.title">
          <div class="case-image" :style="{ background: caseItem.image }"></div>
          <div class="case-body">
            <span class="case-tag">{{ caseItem.category }}</span>
            <h3>{{ caseItem.title }}</h3>
            <p>{{ caseItem.summary }}</p>
          </div>
        </article>
      </div>

      <div class="cta-row text-center mt-4">
        <router-link class="btn btn-primary btn-lg" to="/cases">查看更多案例</router-link>
      </div>
    </div>
  </section>

  <section class="section why-us">
    <div class="container">
      <div class="section-heading">
        <span class="eyebrow">为什么选择我们</span>
        <h2>值得家长信任的专业与温度</h2>
      </div>

      <div class="grid grid-4 advantage-grid">
        <div class="advantage-item" v-for="adv in advantages" :key="adv.title">
          <div class="adv-icon">{{ adv.icon }}</div>
          <h3>{{ adv.title }}</h3>
          <p>{{ adv.text }}</p>
        </div>
      </div>
    </div>
  </section>

  <section class="section section-alt">
    <div class="container contact-banner">
      <div class="banner-copy">
        <span class="eyebrow">咨询入口</span>
        <h2>预约孩子的免费学习评估</h2>
        <p>让我们根据年级、能力与兴趣，给出适合的学习方案。</p>
      </div>

      <form class="mini-form" @submit.prevent="handleSubmit">
        <div class="form-grid">
          <div class="field">
            <label>姓名</label>
            <input v-model="form.name" type="text" placeholder="请输入姓名" />
          </div>
          <div class="field">
            <label>电话</label>
            <input v-model="form.phone" type="tel" placeholder="请输入电话" />
          </div>
          <div class="field">
            <label>孩子年级</label>
            <select v-model="form.grade">
              <option value="">请选择</option>
              <option>小学</option>
              <option>初中</option>
              <option>高中</option>
            </select>
          </div>
          <div class="field full-width">
            <label>咨询内容</label>
            <textarea v-model="form.message" placeholder="请描述孩子的学习需求"></textarea>
          </div>
        </div>
        <button class="btn btn-primary btn-block" type="submit">提交咨询</button>
        <p v-if="submitted" class="success-tip">提交成功！我们将在24小时内与您联系。</p>
      </form>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const services = [
  {
    icon: '⚙️',
    title: '工程项目实训',
    description: '围绕真实项目任务开展动手实践，提升科学、技术、工程与数学综合能力。',
    link: '/services'
  },
  {
    icon: '🏆',
    title: '科创竞赛辅导',
    description: '结合新赛制与竞赛能力提升，帮助孩子在项目设计与表达中建立优势。',
    link: '/services'
  },
  {
    icon: '📘',
    title: '个性化学习规划',
    description: '基于兴趣、能力与阶段目标，制定清晰且可执行的学习成长路径。',
    link: '/services'
  }
]

const cases = [
  {
    title: '智能小车创新挑战',
    category: '项目作品',
    summary: '通过团队协作完成路径规划与传感器应用，提升孩子的工程思维和问题解决能力。',
    image: 'linear-gradient(135deg, #e8f1ff, #cfe3ff)'
  },
  {
    title: 'AI创意设计项目',
    category: '竞赛获奖',
    summary: '围绕智能识别与交互体验展开方案设计，帮助孩子建立技术表达与创新意识。',
    image: 'linear-gradient(135deg, #effaf6, #d6f5e8)'
  },
  {
    title: 'STEAM能力提升成长案例',
    category: '能力提升',
    summary: '从零基础到逐步形成项目执行逻辑，家长反馈明显提升学习自信与学习动力。',
    image: 'linear-gradient(135deg, #fff3df, #ffe7c6)'
  }
]

const advantages = [
  {
    icon: '✅',
    title: '正规企业资质',
    text: '以专业、合法、稳定的运营标准为底层保障，提升家长信任感。'
  },
  {
    icon: '🧠',
    title: '工程项目实战',
    text: '以真实任务驱动学习，让孩子在“做中学”中建立解决问题的底层能力。'
  },
  {
    icon: '👩‍🏫',
    title: '双师型教学团队',
    text: '结合工程背景和教育经验，为孩子提供更高质量的学习支持与成长陪伴。'
  },
  {
    icon: '📈',
    title: '全程学习跟踪',
    text: '从评估、规划到课堂反馈，全流程清晰透明，高效支持家庭决策。'
  }
]

const form = ref({
  name: '',
  phone: '',
  grade: '',
  message: ''
})

const submitted = ref(false)

const handleSubmit = () => {
  if (!form.value.name || !form.value.phone || !form.value.grade) {
    alert('请完整填写姓名、电话和孩子年级。')
    return
  }

  submitted.value = true
  form.value = { name: '', phone: '', grade: '', message: '' }
}
</script>

<style scoped>
.hero-section {
  padding-top: 4.5rem;
  background: linear-gradient(180deg, #f8fbff 0%, #ffffff 100%);
}

.hero-layout {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1.2fr 0.8fr;
  gap: 2rem;
  align-items: center;
  padding: 0 1.2rem;
}

.eyebrow {
  display: inline-block;
  padding: 0.45rem 0.9rem;
  border-radius: 999px;
  background: rgba(0, 82, 204, 0.08);
  color: #0052cc;
  font-weight: 700;
  margin-bottom: 1rem;
  letter-spacing: 0.04em;
  font-size: 0.75rem;
}

.hero-copy h1 {
  margin-bottom: 1rem;
}

.lead {
  font-size: 1.08rem;
  line-height: 1.8;
  max-width: 620px;
  color: #4d4d4d;
}

.hero-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  margin: 2rem 0 1.5rem;
}

.hero-trust {
  display: flex;
  flex-wrap: wrap;
  gap: 0.8rem;
}

.hero-trust span {
  color: #475569;
  background: #f5f8ff;
  border: 1px solid #e8eef9;
  border-radius: 999px;
  padding: 0.55rem 0.9rem;
  font-size: 0.82rem;
}

.hero-visual {
  position: relative;
  min-height: 440px;
}

.feature-card {
  background: white;
  border-radius: 24px;
  box-shadow: 0 20px 44px rgba(15, 23, 42, 0.08);
  border: 1px solid rgba(224, 224, 224, 0.8);
}

.card-main {
  position: absolute;
  inset: 20px 20px 70px 0;
  padding: 2rem;
  background: linear-gradient(135deg, #ffffff, #f4f8ff);
}

.mini-badge {
  display: inline-block;
  color: #0052cc;
  background: rgba(0, 82, 204, 0.08);
  padding: 0.5rem 0.8rem;
  border-radius: 999px;
  font-size: 0.78rem;
  font-weight: 700;
  margin-bottom: 1rem;
}

.card-main ul {
  margin-top: 1.2rem;
  list-style: none;
  display: grid;
  gap: 0.7rem;
}

.card-main li {
  color: #3a3a3a;
  position: relative;
  padding-left: 1.2rem;
}

.card-main li::before {
  content: '•';
  position: absolute;
  left: 0;
  color: #0052cc;
}

.card-float {
  position: absolute;
  right: 0;
  width: 160px;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: #ffffff;
}

.card-top {
  top: 0;
}

.card-bottom {
  bottom: 0;
}

.card-float strong {
  color: #0052cc;
  font-size: 2rem;
  line-height: 1;
}

.card-float span {
  margin-top: 0.5rem;
  color: #4b5563;
  text-align: center;
  font-size: 0.85rem;
}

.metrics-section {
  padding-top: 2rem;
}

.metrics-grid {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1.2rem;
}

.metric-item {
  background: linear-gradient(180deg, #f7faff, #ffffff);
  border: 1px solid rgba(224, 224, 224, 0.7);
  border-radius: 18px;
  padding: 2rem 1rem;
  text-align: center;
}

.metric-item strong {
  display: block;
  font-size: 2.1rem;
  color: #0052cc;
  margin-bottom: 0.5rem;
}

.metric-item span {
  color: #4b5563;
}

.section-heading {
  max-width: 700px;
  margin: 0 auto 2rem;
  text-align: center;
}

.section-heading h2 {
  margin-bottom: 0;
}

.services-overview,
.why-us,
.section-alt {
  background: #ffffff;
}

.section-alt {
  background: #f5f8ff;
}

.service-card,
.case-card,
.advantage-item {
  background: #ffffff;
  border: 1px solid #edf2f7;
  border-radius: 20px;
  padding: 1.8rem 1.4rem;
  box-shadow: 0 10px 24px rgba(15, 23, 42, 0.04);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.service-card:hover,
.case-card:hover,
.advantage-item:hover {
  transform: translateY(-8px);
  box-shadow: 0 18px 28px rgba(15, 23, 42, 0.06);
}

.icon-wrap {
  width: 58px;
  height: 58px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border-radius: 16px;
  background: linear-gradient(135deg, #eaf2ff, #dfeeff);
  font-size: 1.8rem;
  margin-bottom: 1rem;
}

.service-card h3,
.advantage-item h3,
.case-card h3 {
  margin-bottom: 0.7rem;
}

.service-card a {
  display: inline-block;
  margin-top: 1rem;
  font-weight: 700;
}

.case-image {
  height: 180px;
  border-radius: 16px;
  margin-bottom: 1rem;
}

.case-tag {
  display: inline-block;
  background: rgba(0, 82, 204, 0.08);
  color: #0052cc;
  padding: 0.38rem 0.7rem;
  border-radius: 999px;
  font-size: 0.72rem;
  font-weight: 700;
  margin-bottom: 0.8rem;
}

.advantage-grid {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1.2rem;
}

.adv-icon {
  width: 58px;
  height: 58px;
  border-radius: 16px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-size: 1.8rem;
  background: linear-gradient(135deg, #eef7ff, #dff5fc);
  margin-bottom: 1rem;
}

.contact-banner {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 0.9fr 1.1fr;
  gap: 2rem;
  align-items: center;
  background: white;
  border: 1px solid #ecf0f5;
  border-radius: 28px;
  padding: 2rem 1.5rem;
  box-shadow: 0 22px 38px rgba(15, 23, 42, 0.04);
}

.mini-form {
  width: 100%;
}

.form-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 1rem;
}

.field {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.field.full-width {
  grid-column: 1 / -1;
}

.field label {
  font-size: 0.9rem;
  color: #374151;
  font-weight: 600;
}

.field input,
.field select,
.field textarea {
  width: 100%;
  border: 1px solid #e1e7ee;
  border-radius: 12px;
  background: #fff;
  padding: 0.9rem 1rem;
  font: inherit;
  color: #1f2937;
}

.field textarea {
  min-height: 120px;
  resize: vertical;
}

.success-tip {
  margin-top: 0.8rem;
  color: #0f8c53;
  font-weight: 600;
}

@media (max-width: 860px) {
  .hero-layout,
  .contact-banner {
    grid-template-columns: 1fr;
  }

  .card-main {
    inset: 10px 10px 100px 0;
  }
}

@media (max-width: 620px) {
  .form-grid {
    grid-template-columns: 1fr;
  }

  .hero-actions {
    flex-direction: column;
    align-items: stretch;
  }

  .btn {
    width: 100%;
  }
}
</style>
