# 作品集网站 · 部署指南

> 适用对象：把 `portfolio-website/` 这个目录部署到 GitHub Pages。

## 一、内容结构（新版 v2）

| 模块 | 内容 | 对应 anchor |
|---|---|---|
| 封面 | 作品集名 / 姓名 / 组别 / 个人关键词 | `#hero` |
| 4 件作品 | 个人说明书 / 洞察报告 / 招募官网 / 岗位分析 | `#works` |
| AI 成长轨迹 | 6+1 个 AI Skill 时间线 | `#growth` |
| 联系 / Footer | 谢谢阅读 | `#footer` |

## 二、文件清单

```
portfolio-website/
├── index.html              # 主站（约 31 KB，单文件，零外部依赖）
├── README.md               # 本文档
└── assets/                 # 预留（暂无图片资源需要）
```

## 三、推荐部署方式

### 方式 A：根域名 + 独立仓库（推荐，便于推广）

1. 在 GitHub 新建一个仓库，比如 `portfolio` 或 `wuyan-yu`。
2. 把 `index.html` 推到 main 分支根目录。
3. 仓库 → Settings → Pages → Source 选 `main` + `/ (root)`。
4. 等 1-2 分钟，访问 `https://saywaiy.github.io/portfolio/`。

⚠️ 这次比之前多了一道考虑：你已经有了一个 `saywaiy.github.io`（这个仓库名会用根域名）。
所以推荐两种选择：

- A1：新建 `wuyan-yu-portfolio` 仓库，用二级路径 `saywaiy.github.io/wuyan-yu-portfolio/`（不抢根域名）
- A2：把 `saywaiy.github.io` 仓库的 root 切换成新作品集（先备份旧站点所有文件）

### 方式 B：本地预览（不需要 GitHub）

```bash
cd portfolio-website
python3 -m http.server 8080
# 浏览器打开 http://localhost:8080/
```

## 四、自定义

- **作品集名 / 副标题**：编辑 `index.html` 顶部 `<header class="hero">` 部分
- **4 件作品的内容**：编辑 `<article class="work">` 四个区块
- **AI Skill 列表**：编辑 `<section id="growth">` 内 `<div class="skill">`
- **个人关键词**：编辑 `.hero-tags` 中的 `<span class="tag">`
- **配色**：修改 `:root` 里的 CSS 变量即可（不影响布局）

## 五、零依赖说明

- 不引用任何外部字体 CDN（只用系统字体回退链）
- 不引用任何外部 JS / CSS
- 不引用任何图片资源
- 完全离线可打开，直接双击 `index.html` 也能跑

唯一的外部链接：
- `https://saywaiy.github.io/index.html/` —— 旧作品（招募官网），新窗口打开
