# 叁思坦科技 - 完整 Cloudflare Pages 部署指南

## 项目概览
- **项目名称**: 叁思坦科技
- **网站描述**: K12 STEM教育品牌官网
- **技术栈**: Vue 3 + Vite
- **联系人**: 李老师
- **电话/微信**: 17301878401
- **域名**: www.sustain-tech.cn

---

## 一、前置准备

### 1. 注册与账户
- 访问 [Cloudflare](https://dash.cloudflare.com/)
- 注册账户（需要有效邮箱）
- 验证邮箱

### 2. GitHub 账户准备
- 确保项目已推送到 GitHub 仓库 `andylee-arch/sustain-tech`
- 使用 develop 分支作为主分支
- 确保项目根目录包含：
  - `package.json` ✓
  - `vite.config.js` ✓
  - `src/` 目录 ✓
  - `index.html` ✓

---

## 二、本地构建验证

在部署前，先在本地验证项目能否正确构建：

```bash
# 进入项目目录
cd sustain-tech

# 安装依赖
npm install

# 开发模式运行（测试）
npm run dev

# 构建产物
npm run build

# 检查输出目录
ls -la dist/
# 应该看到 index.html 和其他文件
```

---

## 三、Cloudflare Pages 部署步骤

### 步骤 1: 连接 GitHub 仓库

1. 登录 Cloudflare Dashboard
2. 左侧菜单选择 **Pages**
3. 点击 **Create a project**
4. 选择 **Connect to Git**
5. 授权 GitHub 账户（按提示操作）
6. 选择仓库：`andylee-arch/sustain-tech`
7. 点击 **Begin setup**

### 步骤 2: 配置构建设置

在构建配置页面，填写以下信息：

**项目名称**
```
sustain-tech
```

**生产分支**
```
develop
```

**框架预设**
```
Vue
```

**构建命令**
```bash
npm run build
```

**输出目录**
```
dist
```

**环境变量**（可选）
```
无需设置
```

### 步骤 3: 保存并部署

1. 检查配置无误
2. 点击 **Save and Deploy**
3. Cloudflare 会自动：
   - 从 GitHub 拉取代码
   - 执行 `npm install`
   - 执行 `npm run build`
   - 上传 dist 文件夹内容
4. 等待部署完成（通常 1-3 分钟）

### 步骤 4: 查看部署结果

部署成功后，你会看到：
- 一个自动生成的 `*.pages.dev` 域名（如：`sustain-tech.pages.dev`）
- 部署日志和状态

点击生成的域名访问网站进行测试。

---

## 四、绑定自定义域名

### 前置条件
- 已购买并注册域名 `sustain-tech.cn`
- 域名的 DNS 由 Cloudflare 管理

### 4.1 将域名转移到 Cloudflare（如果还未转移）

1. 在 Cloudflare Dashboard 点击 **+ Add a site**
2. 输入域名：`sustain-tech.cn`
3. 选择免费计划
4. Cloudflare 提供新的 Nameserver
5. 登录域名注册商（如阿里云、GoDaddy 等）
6. 将 Nameserver 更新为 Cloudflare 提供的地址
7. 等待 DNS 生效（24-48 小时）

### 4.2 在 Cloudflare Pages 中绑定域名

1. 进入 Cloudflare Pages 项目设置
2. 选择 **Custom domains**
3. 点击 **Add custom domain**
4. 输入域名：`www.sustain-tech.cn`
5. Cloudflare 会自动创建 DNS 记录
6. 点击 **Activate domain**

### 4.3 配置根域名重定向（可选）

if 用户访问 `sustain-tech.cn`（无 www），自动跳转到 `www.sustain-tech.cn`：

1. 在 Cloudflare Dashboard 进入 DNS 设置
2. 找到根域名 (@) 的 A 记录
3. 创建一个 Page Rule：
   - **URL**: `sustain-tech.cn/*`
   - **转发 URL**: `https://www.sustain-tech.cn/$1`
   - **状态码**: 301（永久重定向）

---

## 五、SSL/HTTPS 配置

Cloudflare 默认会自动启用 HTTPS，通常无需手动配置。

验证 HTTPS 是否启用：
1. 进入 Pages 项目设置
2. 选择 **SSL/TLS**
3. 确保 **SSL/TLS 加密模式** 设置为 **Full** 或 **Full (Strict)**

---

## 六、持续部署与更新

### 自动部署
- 每次推送代码到 GitHub `develop` 分支时，Cloudflare 会自动触发构建和部署
- 无需手动操作，通常�� 2-5 分钟内完成

### 手动重新部署
1. 进入 Cloudflare Pages 项目
2. 选择 **Deployments**
3. 找到最新的部署记录
4. 点击 **...** → **Retry deployment**

### 回滚到前版本
1. 在 **Deployments** 中找到需要的版本
2. 点击该版本 → **Rollback to this deployment**

---

## 七、监控与日志

### 查看构建日志
1. 进入 Pages 项目
2. 选择 **Deployments**
3. 点击某个部署记录
4. 查看 **Build logs**

### 常见问题排查

**问题：构建失败**
- 检查 `package.json` 中的依赖是否完整
- 检查 `vite.config.js` 配置是否正确
- 查看 Build logs 中的具体错误信息

**问题：404 错误**
- 确保 `vite.config.js` 中的 `base` 配置正确
- 对于路由应用，在 `vite.config.js` 中添加：
  ```javascript
  export default defineConfig({
    // ...
    build: {
      // ...
    }
  })
  ```
- 在 Cloudflare Pages 项目设置中，添加重定向规则：
  - **URL**: `/*`
  - **转发到**: `/index.html`
  - **状态码**: 200

---

## 八、性能优化建议

### 1. Cloudflare 缓存设置
1. 进入 **Caching** 标签
2. 设置 **Browser Cache TTL**: 30分钟
3. 设置 **Cache Level**: Cache Everything

### 2. 图片优化
- Cloudflare 自动优化图片
- 确保源图片已压缩

### 3. 压缩与 Minify
- 在 Cloudflare **Speed** 设置中
- 启用 **Brotli 压缩**
- 启用 **Auto Minify** (JavaScript, CSS, HTML)

### 4. 分析和监控
- 使用 Cloudflare **Analytics** 查看流量和性能
- 查看 **Real User Monitoring (RUM)** 了解用户体验

---

## 九、安全设置

### 1. 启用 WAF（Web Application Firewall）
- Cloudflare 免费计划默认启用基础 WAF
- 无需额外配置

### 2. DDoS 防护
- Cloudflare 自动提供 DDoS 防护
- 安全性级别设置：**High** 或 **I'm Under Attack**

### 3. 隐私与合规
- 确保已添加隐私政策页面
- 如涉及数据收集，需遵守 GDPR/CCPA 等法规

---

## 十、后续维护

### 日常检查
- 定期检查 Cloudflare Analytics
- 监控网站加载速度和错误率
- 定期更新依赖包：
  ```bash
  npm update
  ```

### 内容更新
- 在本地更新代码
- 推送到 GitHub `develop` 分支
- Cloudflare 自动部署

### 备份
- GitHub 本身即为代码备份
- Cloudflare Pages 自动保留所有部署历史

---

## 十一、快速参考

| 配置项 | 值 |
|--------|-----|
| GitHub 仓库 | andylee-arch/sustain-tech |
| 部署分支 | develop |
| 框架 | Vue |
| 构建命令 | npm run build |
| 输出目录 | dist |
| 域名 | www.sustain-tech.cn |
| 联系人 | 李老师 |
| 电话/微信 | 17301878401 |

---

## 十二、联系支持

如有部署问题：
- **Cloudflare 支持**: https://support.cloudflare.com/
- **GitHub Issues**: https://github.com/andylee-arch/sustain-tech/issues
- **项目联系人**: 李老师 17301878401

---

**部署完成后，网站即可在 www.sustain-tech.cn 访问！** 🎉
