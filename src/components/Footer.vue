<template>
  <footer class="site-footer">
    <div class="container footer-grid">
      <div>
        <div class="brand footer-brand">
          <span class="brand-mark">ST</span>
          <span class="brand-text">叁思坦科技</span>
        </div>
        <p>专注K12 STEM项目式学习，以真实工程项目培养孩子的跨学科解决问题能力。</p>
      </div>

      <div>
        <h4>快速导航</h4>
        <ul>
          <li><router-link to="/">首页</router-link></li>
          <li><router-link to="/services">服务项目</router-link></li>
          <li><router-link to="/team">师资团队</router-link></li>
          <li><router-link to="/cases">学员案例</router-link></li>
          <li><router-link to="/contact">联系我们</router-link></li>
        </ul>
      </div>

      <div>
        <h4>联系我们</h4>
        <ul>
          <li>电话：400-800-8888</li>
          <li>微信：sustain-tech</li>
          <li>邮箱：hello@sustain-tech.cn</li>
          <li>工作时间：9:00-18:00</li>
        </ul>
      </div>

      <div>
        <h4>企业资质</h4>
        <ul>
          <li>正规注册公司</li>
          <li>工程与技术咨询服务</li>
          <li>教育培训与课程开发</li>
        </ul>
      </div>
    </div>

    <div class="footer-bottom">
      <div class="container">
        <p>© 2026 叁思坦科技 保留所有权利</p>
        <p>备案信息：沪ICP备00000000号</p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.site-footer {
  background: #0d1b2a;
  color: rgba(255, 255, 255, 0.9);
  padding-top: 4rem;
  margin-top: 3rem;
}

.footer-grid {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1.5fr 1fr 1fr 1fr;
  gap: 2rem;
  padding: 0 1.2rem 2rem;
}

.footer-brand {
  color: white;
  margin-bottom: 1rem;
}

.site-footer h4 {
  color: white;
  margin-bottom: 1rem;
  font-size: 1.05rem;
}

.site-footer p,
.site-footer li,
.site-footer a {
  color: rgba(255, 255, 255, 0.75);
  font-size: 0.95rem;
}

.site-footer ul {
  list-style: none;
  display: grid;
  gap: 0.6rem;
}

.footer-bottom {
  border-top: 1px solid rgba(255, 255, 255, 0.12);
  padding: 1rem 0;
}

.footer-bottom .container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1.2rem;
  display: flex;
  justify-content: space-between;
  gap: 1rem;
  flex-wrap: wrap;
}

@media (max-width: 860px) {
  .footer-grid {
    grid-template-columns: 1fr 1fr;
  }
}

@media (max-width: 560px) {
  .footer-grid {
    grid-template-columns: 1fr;
  }
}
</style>
