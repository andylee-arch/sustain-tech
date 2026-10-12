# Cloudflare Pages 部署快速开始指南

## 5 分钟快速部署

### 第一步：本地准备（2 分钟）

```bash
# 确保代码已提交到 develop 分支
git add .
git commit -m "Final version ready for deployment"
git push origin develop

# 本地验证构建
npm run build
ls dist/  # 确保输出目录存在
```

### 第二步：Cloudflare 部署（3 分钟）

1. **访问 Cloudflare**: https://dash.cloudflare.com/
2. **登录/注册**
3. **选择 Pages**
4. **Create a project** → **Connect to Git**
5. **选择仓库**: andylee-arch/sustain-tech
6. **填写部署配置**:
   - 生产分支：`develop`
   - 框架：`Vue`
   - 构建命令：`npm run build`
   - 输出目录：`dist`
7. **保存并部署**

### 第三步：绑定域名

1. 进入 Pages 项目 → **Custom domains**
2. **Add custom domain**
3. 输入：`www.sustain-tech.cn`
4. **Activate**

**完成！** 网站现已在 www.sustain-tech.cn 上线 🎉

---

## 重要配置项

| 项目 | 值 |
|-----|----|
| GitHub 仓库 | andylee-arch/sustain-tech |
| 分支 | develop |
| 构建命令 | npm run build |
| 输出目录 | dist |
| 框架 | Vue |
| 域名 | www.sustain-tech.cn |

---

## 常见问题

### Q: 如何更新网站内容？
A: 推送代码到 `develop` 分支，Cloudflare 会自动部署。

### Q: 部署失败怎么办？
A: 查看 Cloudflare Pages 中的 Build logs，检查错误信息。

### Q: 如何回滚到上一版本？
A: 进入 Deployments，选择之前的版本，点击 Rollback。

---

## 联系方式

**李老师**
📱 17301878401（电话/微信）
📧 hello@sustain-tech.cn
⏰ 工作时间：9:00-18:00

---

**需要详细指南？** 查看 `DEPLOYMENT.md`
