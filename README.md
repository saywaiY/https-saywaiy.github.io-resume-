# 个人简历网站部署指南

这套站点是单文件 HTML + 1 个 PDF 资源，零外部依赖，可以直接放到任何静态托管平台上。下面以 **GitHub Pages** 为例，介绍两种最常见的部署方式。

## 目录结构

```
resume-website/
├── index.html                    # 站点主文件
├── assets/
│   └── 吴瑶誉简历_品牌营销实习生.pdf   # PDF 简历（点击「下载 PDF 简历」即下此文件）
└── README.md
```

---

## 方式 A：用 `username.github.io` 根域名（推荐 · 当前已有站点）

`https://saywaiy.github.io/` 已经在使用了 —— 之前部署的是北辰青年招募官网。

如果你希望这个简历站挂在**根域名**（`https://saywaiy.github.io/`），需要先把旧仓库的 `index.html` 备份下来，再用本目录覆盖。

如果你希望简历站和旧站并存，建议采用方式 B（新建一个项目仓库 + 二级路径）。

---

## 方式 B：新建项目仓库，用二级路径（推荐 · 不影响旧站）

新建仓库名例如 `resume-site`（仓库名随意，只要不和已有项目同名）。

### 步骤 1：创建新仓库

1. 打开 https://github.com/new
2. Repository name 填 `resume-site`（或者你想叫的名字）
3. 选 **Public**（GitHub Pages 免费版只支持 Public 仓库）
4. 不要勾选 Add a README / .gitignore / license（保持空仓库）
5. 点击 Create repository

### 步骤 2：把本地目录推到 GitHub

在终端里执行：

```bash
cd /Users/wuyaoyu/Desktop/求职skill/output/resume-website

git init
git add .
git commit -m "init: 个人简历网站"
git branch -M main
git remote add origin git@github.com:saywaiy/resume-site.git   # 把这里换成你的仓库地址
git push -u origin main
```

> 如果你之前没用过 SSH key，HTTPS 也行：
> `git remote add origin https://github.com/saywaiy/resume-site.git`

### 步骤 3：开启 GitHub Pages

1. 打开仓库页面 → **Settings** → 左侧栏 **Pages**
2. Source 选 **Deploy from a branch**
3. Branch 选 `main`，目录 `/`（root），保存
4. 等待 1-2 分钟，页面顶部会显示一行绿色的"Your site is live at..."
5. 访问地址类似：
   - 项目仓库：`https://saywaiy.github.io/resume-site/`
   - 用户页仓库：`https://saywaiy.github.io/`（如果仓库名是 `username.github.io`）

### 步骤 4：替换 PDF 链接路径

如果走方式 B 的项目仓库路径（`/resume-site/`），PDF 链接需要从

```html
<a href="assets/吴瑶誉简历_品牌营销实习生.pdf" download>
```

改成

```html
<a href="resume-site/assets/吴瑶誉简历_品牌营销实习生.pdf" download>
```

或者更稳妥的相对写法 `./assets/吴瑶誉简历_品牌营销实习生.pdf`（推荐，相对路径对 GitHub Pages 二进制路径是稳定的）。

> 我已经默认用了相对路径 `./assets/...`，不需要改。

### 步骤 5：自定义域名（可选）

如果你有自己的域名（例如 `fanfan.works`），可以在 Settings → Pages → Custom domain 里填写，再去域名服务商加一条 CNAME 指向 `saywaiy.github.io`。

---

## 方式 C：本地预览（在推到 GitHub 之前自己先看效果）

```bash
cd /Users/wuyaoyu/Desktop/求职skill/output/resume-website
python3 -m http.server 8000
```

然后浏览器打开 `http://localhost:8000/` 即可。

按 `Ctrl + C` 停止服务。

---

## 后续怎么更新内容

每次改了 `index.html` 里的内容，只需要：

```bash
cd /Users/wuyaoyu/Desktop/求职skill/output/resume-website
git add .
git commit -m "update: 修改了 XX"
git push
```

GitHub Pages 会在几秒内自动重新部署，刷新浏览器就能看到最新版本。

---

## 一些建议

- **PDF 文件名是中文**：`assets/吴瑶誉简历_品牌营销实习生.pdf` 在 GitHub 仓库里没问题，但下载到不同操作系统的客户端时偶尔会出现编码差异。如果未来想做得更稳，可以把 PDF 改成英文文件名（如 `assets/resume.pdf`），同时把 `index.html` 里所有 `href` 引用统一改成英文路径。
- **隐私**：联系信息（邮箱、手机号）目前都是公开的。如果你想更稳妥，可以只留邮箱，并考虑去掉手机号。
- **暗色模式**：右上角小按钮可切换，会自动记忆。

---

有任何问题随时问我。