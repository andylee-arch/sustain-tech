@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap');

:root {
  --primary: #0d5bd7;
  --primary-strong: #0a46b4;
  --primary-soft: #edf4ff;
  --secondary: #1ec6d6;
  --accent: #ff8a3d;
  --text: #172033;
  --text-soft: #536179;
  --bg: #f7f9fd;
  --bg-strong: #eef5ff;
  --line: #e8edf7;
  --success: #0e8a5f;
  --shadow-lg: 0 20px 45px rgba(17, 24, 39, 0.1);
  --shadow-md: 0 10px 28px rgba(15, 23, 42, 0.06);
  --radius-xl: 28px;
  --radius-lg: 22px;
  --radius-md: 16px;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  font-family: 'Inter', 'PingFang SC', 'Microsoft YaHei', sans-serif;
  background:
    radial-gradient(circle at top left, rgba(13, 91, 215, 0.06), transparent 30%),
    linear-gradient(180deg, #fcfdff 0%, #f7f9fd 100%);
  color: var(--text);
  line-height: 1.7;
  -webkit-font-smoothing: antialiased;
  text-rendering: optimizeLegibility;
}

img {
  max-width: 100%;
  display: block;
}

button,
input,
select,
textarea {
  font: inherit;
}

a {
  color: var(--primary);
  text-decoration: none;
  transition: color 0.2s ease, transform 0.2s ease;
}

a:hover {
  color: var(--secondary);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  width: min(1200px, calc(100% - 2rem));
}

.section {
  padding: 5rem 0;
}

.section-alt {
  background: linear-gradient(180deg, rgba(237, 244, 255, 0.8), rgba(247, 249, 253, 0.7));
}

.eyebrow {
  display: inline-block;
  padding: 0.5rem 0.9rem;
  border-radius: 999px;
  background: rgba(13, 91, 215, 0.08);
  color: var(--primary);
  font-weight: 700;
  margin-bottom: 1rem;
  letter-spacing: 0.04em;
  font-size: 0.75rem;
}

h1, h2, h3, h4, h5, h6 {
  line-height: 1.2;
  color: #101827;
}

h1 {
  font-size: clamp(2.4rem, 5vw, 4.2rem);
  font-weight: 800;
  letter-spacing: -0.04em;
}

h2 {
  font-size: clamp(1.9rem, 3vw, 2.8rem);
  font-weight: 800;
  margin-bottom: 1rem;
  letter-spacing: -0.03em;
}

h3 {
  font-size: clamp(1.15rem, 2vw, 1.6rem);
  font-weight: 700;
}

p {
  color: var(--text-soft);
  margin-bottom: 0;
}

.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.9rem 1.5rem;
  border-radius: 14px;
  font-weight: 700;
  border: 1px solid transparent;
  transition: all 0.25s ease;
  cursor: pointer;
  white-space: nowrap;
}

.btn:hover {
  transform: translateY(-2px);
}

.btn-primary {
  background: linear-gradient(135deg, var(--primary), #2d7dff);
  color: white;
  box-shadow: 0 10px 18px rgba(13, 91, 215, 0.22);
}

.btn-primary:hover {
  background: linear-gradient(135deg, var(--primary-strong), var(--primary));
  color: white;
}

.btn-outline {
  border-color: rgba(13, 91, 215, 0.2);
  background: rgba(255, 255, 255, 0.6);
  color: var(--primary);
  box-shadow: 0 8px 20px rgba(13, 91, 215, 0.08);
}

.btn-outline:hover {
  background: rgba(13, 91, 215, 0.06);
  color: var(--primary);
}

.btn-sm {
  padding: 0.72rem 1rem;
  font-size: 0.92rem;
}

.btn-lg {
  padding: 1.05rem 1.6rem;
  font-size: 1rem;
}

.btn-block {
  width: 100%;
}

.grid {
  display: grid;
  gap: 1.5rem;
}

.grid-2 { grid-template-columns: repeat(2, minmax(0, 1fr)); }
.grid-3 { grid-template-columns: repeat(3, minmax(0, 1fr)); }
.grid-4 { grid-template-columns: repeat(4, minmax(0, 1fr)); }

.page-wrap {
  min-height: 60vh;
}

.narrow-copy p,
.section-heading p {
  max-width: 760px;
  margin: 0 auto;
}

.text-center {
  text-align: center;
}

.mt-4 {
  margin-top: 2rem;
}

@media (max-width: 920px) {
  .grid-3, .grid-4 {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (max-width: 640px) {
  .grid-2, .grid-3, .grid-4 {
    grid-template-columns: 1fr;
  }

  .section {
    padding: 4rem 0;
  }

  .btn {
    width: 100%;
  }
}
