# IEEE-suite-skills

> **IEEE 期刊投稿一条龙 Claude Code / Codex CLI skill 套件。**
> 10 个 sub-skill 覆盖从选题选刊到写作、引用、图表、LaTeX 模板、数据可用性、审稿回复的端到端流程，全部锚定 IEEE Author Center / IEEE Editorial Style Manual / IEEEtran 官方规范。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Skills: 10](https://img.shields.io/badge/sub--skills-10-blue.svg)](./skills/)
[![Status: v0.1.0](https://img.shields.io/badge/status-v0.1.0%20pending-orange.svg)](./CHANGELOG.md)
[![IEEE Aligned](https://img.shields.io/badge/aligned-IEEE%20Author%20Center-005CC8.svg)](https://journals.ieeeauthorcenter.ieee.org/)

> 🇬🇧 English: see [README.en.md](./README.en.md)

---

## ✨ 一句话定位

**仿 [`Yuan1z0825/nature-skills`](https://github.com/Yuan1z0825/nature-skills) 的工程矩阵，把内容全部替换为 IEEE 期刊规范**——给 IEEE Transactions / Letters / Conference 投稿者一套可被 Claude Code、Codex CLI 直接调用的端到端 skill 集合。

不同于 [`cookjohn/ieee-skills`](https://github.com/cookjohn/ieee-skills) 专注 IEEE Xplore 网页自动化（搜索 / 浏览 / 下载 / 导出），本仓库聚焦**手稿层**的写作规范、引用合规、图表对齐、LaTeX 排版、审稿回应——两者互补、可以同时用。

---

## 📦 10 个 sub-skill 矩阵

| # | Skill | 状态 | 一句话能力 | 触发关键词 |
|---|---|---|---|---|
| 1 | [ieee-writing](./skills/ieee-writing/) | Stable | 按 IEEE Editorial Style Manual 写作；§I-§VI 结构；≤250 字摘要；5-8 keywords | `IEEE journal manuscript`, `IEEE Editorial Style Manual` |
| 2 | [ieee-polishing](./skills/ieee-polishing/) | Stable | IEEE 房屋风格打磨：被动语态适度、SI 单位、缩写首次展开、`Fig. N` 缩写 | `IEEE polishing`, `IEEE house style` |
| 3 | [ieee-figure](./skills/ieee-figure/) | Stable | 图表规范：单栏 88.9mm / 双栏 182mm / line art ≥600 DPI / 字号 ≥8pt / TIFF 或 vector PDF | `IEEE figure`, `IEEE graphics requirements` |
| 4 | [ieee-citation](./skills/ieee-citation/) | Stable | `[N]` 编号引用 + IEEEtran.bst BibTeX 模板 + 月份缩写 + `[1]–[5]` 合并规则 | `IEEEtran bibtex`, `IEEE numeric citation` |
| 5 | [ieee-response](./skills/ieee-response/) | Stable | IEEE single-blind 审稿回复：逐点 R&R 矩阵、不编造数据、`AUTHOR_INPUT_NEEDED` 兜底 | `IEEE peer review response`, `IEEE rebuttal` |
| 6 | [ieee-reader](./skills/ieee-reader/) | Beta | IEEE PDF / Xplore → 结构化 Markdown（章节/图表/`[N]` 引用保号） | `IEEE PDF reader`, `IEEE Xplore extract` |
| 7 | [ieee-academic-search](./skills/ieee-academic-search/) | Beta | 编排 IEEE Xplore + DBLP + Crossref；arXiv 预印本政策提示 | `IEEE Xplore search`, `IEEE related work` |
| 8 | [ieee-data](./skills/ieee-data/) | Beta | IEEE Research Reproducibility：DataPort/Zenodo/Figshare 选择 + 数据可用性声明模板 | `IEEE data availability`, `IEEE DataPort` |
| 9 | [ieee-template](./skills/ieee-template/) | Beta | IEEEtran.cls 模板生成 + PDF eXpress 合规检查 | `IEEEtran template`, `IEEE PDF eXpress` |
| 10 | [ieee-venue-selector](./skills/ieee-venue-selector/) | Beta | 12 IEEE Transactions + 8 顶会矩阵；page limit / blind / overlength fee 决策 | `IEEE venue selection`, `IEEE journal recommendation` |

> 每个 sub-skill 的目录都按统一规范组织：`SKILL.md` 主文件 + `README.md` 简介 + `references/` IEEE 官方资料 + `tests/rubric.md` 6 维度评估 + ≥3 个 fixture 用例。

---

## 🚀 为什么用

- **IEEE 真规范**——每条规则都引用 IEEE Author Center / IEEE Editorial Style Manual / IEEEtran 官方源，没有"AI 想象的学术 best practice"
- **跨 Claude + Codex**——SKILL.md 用 Agent Skills 标准格式，本地 Claude Code 和远程 Codex CLI 都能加载
- **10 个 sub-skill 协同**——`ieee-venue-selector` → `ieee-writing` → `ieee-citation` → `ieee-figure` → `ieee-template` → `ieee-response`，端到端链路覆盖
- **质量门控**——每个 sub-skill 都有 6 维度 rubric.md（Completeness / Traceability / Factuality / IEEE-fit / Actionability / Cross-skill integration），≥24/30 才上线
- **不抄不编**——文档结构仿 nature-skills，但**所有 IEEE 内容独立著作**，每个 URL 都经 WebFetch 验证

---

## ⚡ Quick start

### 选项 1：Codex 直接安装（推荐）

```bash
git clone https://github.com/XiansenWu954/IEEE-suite-skills.git
cd IEEE-suite-skills
mkdir -p ~/.codex/skills
# 装单个 skill
cp -R skills/ieee-writing ~/.codex/skills/
# 或一次装全部 10 个
for d in skills/ieee-*; do cp -R "$d" ~/.codex/skills/; done
```

### 选项 2：Claude Code subagent wrapper

```bash
git clone https://github.com/XiansenWu954/IEEE-suite-skills.git ~/ai-skills/IEEE-suite-skills
mkdir -p ~/.claude/agents
# 对每个想用的 skill 创建一个 wrapper
cat > ~/.claude/agents/ieee-writing.md <<'EOF'
---
name: ieee-writing
description: Author IEEE journal manuscripts conforming to IEEE Editorial Style Manual.
---
First read ~/ai-skills/IEEE-suite-skills/skills/ieee-writing/SKILL.md, then follow its workflow.
EOF
```

详见 [install.md](./install.md) 的完整三路径说明。

### 选项 3：直接复制到任意工作树

```bash
git clone https://github.com/XiansenWu954/IEEE-suite-skills.git
# 把 skills/ieee-* 整目录搬到你项目的 .claude/skills/ 或 .codex/skills/
cp -R IEEE-suite-skills/skills/ieee-writing ./.claude/skills/
```

---

## 🧭 一条龙工作流（典型 IEEE 投稿路径）

```
   ┌────────────────────┐
   │ 选题 + 选刊        │ ──→ ieee-venue-selector  (12 期刊 + 8 顶会矩阵 → 推荐 venue)
   └────────────────────┘
              ↓
   ┌────────────────────┐
   │ 文献调研            │ ──→ ieee-academic-search (Xplore + DBLP + Crossref)
   │                     │      ieee-reader        (读已有 IEEE 论文)
   └────────────────────┘
              ↓
   ┌────────────────────┐
   │ 写正文              │ ──→ ieee-writing   (§I-§VI 结构 + 摘要 keywords)
   │                     │      ieee-polishing (IEEE 房屋风格)
   │                     │      ieee-citation  ([N] + IEEEtran.bst)
   │                     │      ieee-figure    (单/双栏尺寸 + DPI + 字号)
   │                     │      ieee-data      (DataPort/Zenodo 声明)
   └────────────────────┘
              ↓
   ┌────────────────────┐
   │ LaTeX 排版          │ ──→ ieee-template (IEEEtran.cls + PDF eXpress)
   └────────────────────┘
              ↓
   ┌────────────────────┐
   │ 投稿 → 审稿意见     │
   └────────────────────┘
              ↓
   ┌────────────────────┐
   │ Reviewer 回复       │ ──→ ieee-response (单盲 R&R 矩阵 + 不编造)
   └────────────────────┘
```

---

## 🆚 与同类项目对比

| 项目 | 定位 | 覆盖 |
|---|---|---|
| [Yuan1z0825/nature-skills](https://github.com/Yuan1z0825/nature-skills) | Nature 系生物医学 | 9 skills；写作 + 图表 + 引用，但仅 Nature 风格 |
| [cookjohn/ieee-skills](https://github.com/cookjohn/ieee-skills) | IEEE Xplore 浏览器自动化 | 9 skills；搜索 / 下载 / 导出 BibTeX |
| **IEEE-suite-skills**（本仓库） | **IEEE 期刊手稿层一条龙** | **10 skills**；写作 / 引用 / 图表 / LaTeX / 审稿回应 / 数据声明 / 期刊选择 |

三个仓库可同时启用，互不冲突。

---

## 📐 工程规范

- **SKILL.md schema**：所有 sub-skill 用统一 frontmatter + 8 节固定章节结构。详见 [.briefs/SKILL_schema.md](./.briefs/SKILL_schema.md)（如可访问；该目录在 maintainer 工作流中保留）
- **质量门控**：每个 sub-skill 6 维度 rubric，≥24/30 才并入 main
- **死链 CI**：`.github/workflows/check-links.yml` 每周扫描所有 IEEE 官方 URL；URL 失效自动开 issue
- **年度审查**：IEEE 政策（page limit / overlength fee / blind 模式）每年变；CHANGELOG 标记 `Verified: YYYY-MM-DD`，过期 12 个月自动 flag

---

## 🗺️ Roadmap

- [ ] v0.1.0 首发：10 个 sub-skill 全交付 + awesome-claude-skills PR
- [ ] v0.2.0：补 `ieee-cover-letter` + `ieee-orcid` + IEEE Access OA 工作流
- [ ] v0.3.0：与 [`cookjohn/ieee-skills`](https://github.com/cookjohn/ieee-skills) 集成路径 —— `ieee-academic-search` 调用其 Xplore 自动化做实际抓取

---

## 🤝 贡献

欢迎补充新 sub-skill、更新过期的 IEEE 数据（`journal-matrix.csv` / `conference-matrix.csv`）、增加 fixture 用例。详见 [CONTRIBUTING.md](./CONTRIBUTING.md)。

代码 + 文档 PR 都走 [Conventional Commits](https://www.conventionalcommits.org/)：`feat(ieee-citation): ...` / `fix(ieee-figure): ...` / `docs: ...`。

---

## 📜 License

[MIT](./LICENSE)。IEEE 官方 PDF 文档仅以 URL 形式引用，不在本仓库重发布（© IEEE）。`IEEEtran.cls` 来自 CTAN，按 LPPL 协议附带。

---

## 🙏 致谢

- [`Yuan1z0825/nature-skills`](https://github.com/Yuan1z0825/nature-skills) —— 工程结构模板的灵感来源
- [`cookjohn/ieee-skills`](https://github.com/cookjohn/ieee-skills) —— IEEE Xplore 自动化的互补实现
- IEEE Author Center —— 所有规范的权威源头
