---
slug: deckify
---

## 使用场景

- 从任意品牌网站 URL 提取一份完整的 Design System（颜色、字体、logo、调性）
- 生成一份贴合品牌视觉语言的 9 页 HTML deck，浏览器直接打开
- 把品牌规范建一次，之后每一份 deck 都让 AI 基于它生成
- 让 slides 套上某个公司的真实视觉语言，而不是千篇一律的 AI 风格
- 产出「活的 HTML」slides —— 可动画、可查询、可粘贴 —— 而非 `.pptx` 二进制

## 工作原理

- **看着学，不靠 prompt 编造**：像设计师一样浏览品牌网站 —— 首页、关于、媒体页 —— 从证据里读出真实的颜色、字体、logo 和调性
- **产出可复用的资产**：是一份 Design System markdown，不是一次性 deck。改一次，下游所有 deck 跟着升级
- **自检自己的工作**：跑 11 项确定性硬检查（尺寸、logo 可见性、移动端折叠、无 emoji、12px 可读下限），再用 6 项视觉标准给自己打分 —— 哪项低就改哪项
- **知道哪些永远不能变**：40+ 条工程规则（适配契约、单吸收器规则、移动端 inline-flex catch-all、logo-as-SVG-symbol 模式）烙进核心；每个品牌只有真该变的视觉部分在变

## 示例

```bash
# 安装 skill（支持 Claude Code、Codex、Cursor 等 70+ 个 agent）
npx skills add seacen/deckify

# 然后对任意品牌 URL 触发：
use deckify on https://www.tiffany.com
```

5–10 分钟，你拿到两份能复利的资产：
一份 Design System `.md`（可复用的主交付物）和一份验证用的 `.html` demo deck（证明规范可工作），都落在 `~/deckify/decks/<品牌>/`。

## 注意事项

- 依赖独立的 [`agent-browser`](https://github.com/vercel-labs/agent-browser) CLI 来做渲染后 DOM 侦察、computed styles 和截图 —— `scripts/setup.py` 会检查它并给出对应平台的安装命令
- 所有输出落在 `~/deckify/`，与你从哪个目录运行无关
- 支持英文和中文 deck，各有维护的姊妹模板
- 协议：PolyForm Noncommercial 1.0.0 —— 个人、教育、研究和非商业用途免费；商业用途需单独授权
