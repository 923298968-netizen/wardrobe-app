# GitHub Pages 部署指南

## 方法 1：GitHub CLI（推荐，2分钟完成）

```bash
# 1. 安装 GitHub CLI
brew install gh

# 2. 登录
gh auth login
# 选择 GitHub.com
# 选择 HTTPS
# 选择 Login with a web browser

# 3. 创建仓库并推送
cd /Users/jaya/WorkBuddy/Claw/wardrobe-app
gh repo create wardrobe-app --public --source=. --push

# 4. 启用 GitHub Pages
gh api repos/:owner/wardrobe-app/pages -X PUT -f source[branch]=main -f source[path]/

# 5. 等待约 30 秒，访问
# https://你的用户名.github.io/wardrobe-app/
```

---

## 方法 2：手动创建（3分钟完成）

### 步骤 1：创建 GitHub 仓库

1. 访问：https://github.com/new
2. 仓库名：`wardrobe-app`
3. 设为 **Public**（Public 才能免费用 GitHub Pages）
4. **不要**勾选 "Initialize this repository with a README"
5. 点击 "Create repository"

### 步骤 2：推送代码

```bash
cd /Users/jaya/WorkBuddy/Claw/wardrobe-app
git remote add origin https://github.com/你的用户名/wardrobe-app.git
git push -u origin main
```

### 步骤 3：启用 GitHub Pages

1. 进入仓库 → Settings → 左侧 "Pages"
2. "Build and deployment" → "Source" 选择 **Deploy from a branch**
3. "Branch" 选择 **main**，文件夹选 **/(root)**
4. 点击 "Save"

等待约 30-60 秒，顶部会显示你的网站地址：
```
https://你的用户名.github.io/wardrobe-app/
```

---

## 部署后验证

1. 访问 `https://你的用户名.github.io/wardrobe-app/preview.html`
2. 检查首页、搭配、衣橱、添加、记录、报告 6 个 Tab 是否正常
3. 测试手机 Safari 打开后「添加到主屏幕」功能

---

## 更新代码后重新部署

```bash
git add .
git commit -m "update: 更新说明"
git push
```

GitHub Pages 会自动部署，约 30 秒后生效。

---

## 自定义域名（可选）

如果你有自己的域名，可以在 Pages 设置中绑定，步骤：
1. Settings → Pages → Custom domain
2. 输入域名，按照提示配置 DNS CNAME 记录
