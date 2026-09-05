# 简历网站制作总览

## 本次交付

把当前最新的《品牌营销实习生》简历内容，重新做成一个**清新简约大气风**的单页响应式网站，可直接部署到 GitHub Pages。

## 文件清单

| 文件 | 说明 |
|---|---|
| `index.html` | 单文件网站（HTML + CSS + JS，零外部依赖，可直接丢 GitHub Pages） |
| `assets/吴瑶誉简历_品牌营销实习生.pdf` | 下载按钮对应的 PDF 简历 |
| `README.md` | GitHub Pages 部署指南 |
| `preview_desktop.png` | 桌面端 1440px 宽预览图 |

## 设计特点

- 白底 + 墨绿（#1f4e5f）主色 + 暖橙（#d97757）数字高亮
- 桌面左侧固定导航，点击自动高亮当前章节
- 移动端汉堡菜单折叠
- 右上角可切换明暗主题，偏好自动记忆
- 5 个内容版块：关于 / 教育背景 / 实习经历 / 项目实践 / 技能工具
- 顶部 Hero + 底部联系区，均含「下载 PDF 简历」「发邮件」按钮

## 部署方式

见 `README.md`。最推荐：新建一个独立仓库（如 `resume-site`），推上去后在 GitHub Settings → Pages 开启 `main` 分支部署，网址类似 `https://saywaiy.github.io/resume-site/`。这样既不影响 `saywaiy.github.io` 根域名下已有的北辰青年官网。

## 验证结果

- 本地 `python3 -m http.server` 测试：HTML 200、PDF 下载 200
- Playwright Chromium 桌面端 1440px 截图：文字、颜色、两栏布局均正确
- Playwright 移动端 390px 截图：响应式布局正常
