<template>
  <header class="site-header">
    <div class="container header-inner">
      <router-link class="brand" to="/" aria-label="叁思坦科技首页">
        <span class="brand-mark">ST</span>
        <span class="brand-text">叁思坦科技</span>
      </router-link>

      <nav class="main-nav" :class="{ open: menuOpen }">
        <router-link to="/" @click="closeMenu">首页</router-link>
        <router-link to="/services" @click="closeMenu">服务项目</router-link>
        <router-link to="/team" @click="closeMenu">师资团队</router-link>
        <router-link to="/cases" @click="closeMenu">学员案例</router-link>
        <router-link to="/contact" @click="closeMenu">联系我们</router-link>
      </nav>

      <div class="header-actions">
        <router-link class="btn btn-primary btn-sm" to="/contact">免费咨询</router-link>
        <button class="menu-toggle" @click="toggleMenu" aria-label="打开菜单">
          <span></span>
          <span></span>
          <span></span>
        </button>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue'

const menuOpen = ref(false)

const toggleMenu = () => {
  menuOpen.value = !menuOpen.value
}

const closeMenu = () => {
  menuOpen.value = false
}
</script>

<style scoped>
.site-header {
  position: sticky;
  top: 0;
  z-index: 1000;
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid rgba(224, 224, 224, 0.8);
}

.header-inner {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 82px;
  padding: 0 1.2rem;
}

.brand {
  display: inline-flex;
  align-items: center;
  gap: 0.75rem;
  color: #0d1b2a;
  font-weight: 700;
  font-size: 1.1rem;
}

.brand-mark {
  width: 38px;
  height: 38px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border-radius: 12px;
  background: linear-gradient(135deg, #0052cc, #00a3e0);
  color: white;
  font-size: 0.9rem;
  box-shadow: 0 8px 20px rgba(0, 82, 204, 0.2);
}

.main-nav {
  display: flex;
  align-items: center;
  gap: 1.6rem;
}

.main-nav a {
  color: #2a2a2a;
  font-size: 0.96rem;
  font-weight: 500;
  position: relative;
}

.main-nav a::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -8px;
  width: 100%;
  height: 2px;
  background: #0052cc;
  transform: scaleX(0);
  transform-origin: center;
  transition: transform 0.3s ease;
}

.main-nav a:hover::after,
.main-nav a.router-link-exact-active::after {
  transform: scaleX(1);
}

.header-actions {
  display: flex;
  align-items: center;
  gap: 0.6rem;
}

.menu-toggle {
  display: none;
  width: 42px;
  height: 42px;
  border-radius: 10px;
  border: 1px solid #dfe6ee;
  background: white;
  cursor: pointer;
}

.menu-toggle span {
  display: block;
  width: 20px;
  height: 2px;
  background: #1f2937;
  margin: 4px auto;
  border-radius: 2px;
}

@media (max-width: 860px) {
  .menu-toggle {
    display: block;
  }

  .main-nav {
    position: absolute;
    top: 82px;
    left: 1rem;
    right: 1rem;
    flex-direction: column;
    align-items: flex-start;
    gap: 1rem;
    padding: 1rem 1.2rem;
    background: #ffffff;
    border: 1px solid #edf2f7;
    border-radius: 16px;
    box-shadow: 0 18px 40px rgba(31, 41, 55, 0.08);
    opacity: 0;
    pointer-events: none;
    transform: translateY(-8px);
    transition: all 0.25s ease;
  }

  .main-nav.open {
    opacity: 1;
    pointer-events: auto;
    transform: translateY(0);
  }

  .header-actions .btn {
    display: none;
  }
}
</style>
