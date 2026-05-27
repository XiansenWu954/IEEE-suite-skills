# IEEE-suite-skills

> **One-stop Claude Code / Codex CLI skill suite for IEEE journal submission.**
> 10 sub-skills covering the end-to-end workflow from venue selection to writing, citation, figures, LaTeX templates, data availability, and reviewer response — all anchored in the IEEE Author Center / IEEE Editorial Style Manual / IEEEtran official spec.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Skills: 10](https://img.shields.io/badge/sub--skills-10-blue.svg)](./skills/)
[![Status: v0.1.0](https://img.shields.io/badge/status-v0.1.0%20pending-orange.svg)](./CHANGELOG.md)
[![IEEE Aligned](https://img.shields.io/badge/aligned-IEEE%20Author%20Center-005CC8.svg)](https://journals.ieeeauthorcenter.ieee.org/)

> 🇨🇳 中文: see [README.md](./README.md)

---

## ✨ Pitch

Following the engineering shape of [`Yuan1z0825/nature-skills`](https://github.com/Yuan1z0825/nature-skills), but with **all content rewritten for IEEE**. Gives IEEE Transactions / Letters / Conference authors a coherent set of skills that Claude Code and Codex CLI can invoke directly.

Distinct from [`cookjohn/ieee-skills`](https://github.com/cookjohn/ieee-skills), which automates the IEEE Xplore web UI (search / browse / download / export). We work at the **manuscript layer**: writing conformance, citation compliance, figure spec, LaTeX typesetting, reviewer response. Both repos are complementary; use them together.

---

## 📦 The 10-sub-skill matrix

| # | Skill | Status | One-line capability | Trigger keywords |
|---|---|---|---|---|
| 1 | [ieee-writing](./skills/ieee-writing/) | Stable | Author IEEE journal manuscripts per Editorial Style Manual; §I-§VI structure; ≤250-word abstract; 5-8 keywords | `IEEE journal manuscript`, `IEEE Editorial Style Manual` |
| 2 | [ieee-polishing](./skills/ieee-polishing/) | Stable | IEEE house-style polish: voice balance, SI units, first-use abbreviation expansion, `Fig. N` not `Figure N` | `IEEE polishing`, `IEEE house style` |
| 3 | [ieee-figure](./skills/ieee-figure/) | Stable | Figure spec: single-col 88.9mm / double-col 182mm / line art ≥600 DPI / fonts ≥8pt / TIFF or vector PDF | `IEEE figure`, `IEEE graphics requirements` |
| 4 | [ieee-citation](./skills/ieee-citation/) | Stable | `[N]` numeric refs + IEEEtran.bst-conforming BibTeX + month abbreviations + `[1]–[5]` compaction | `IEEEtran bibtex`, `IEEE numeric citation` |
| 5 | [ieee-response](./skills/ieee-response/) | Stable | IEEE single-blind reviewer response: point-by-point R&R matrix, no fabrication, `AUTHOR_INPUT_NEEDED` token | `IEEE peer review response`, `IEEE rebuttal` |
| 6 | [ieee-reader](./skills/ieee-reader/) | Beta | IEEE PDF / Xplore → structured Markdown (preserves section / figure / citation numbering) | `IEEE PDF reader`, `IEEE Xplore extract` |
| 7 | [ieee-academic-search](./skills/ieee-academic-search/) | Beta | Orchestrates IEEE Xplore + DBLP + Crossref; surfaces IEEE arXiv preprint policy | `IEEE Xplore search`, `IEEE related work` |
| 8 | [ieee-data](./skills/ieee-data/) | Beta | IEEE Research Reproducibility: DataPort/Zenodo/Figshare selection + data-availability statement templates | `IEEE data availability`, `IEEE DataPort` |
| 9 | [ieee-template](./skills/ieee-template/) | Beta | IEEEtran.cls template generation + PDF eXpress compliance check | `IEEEtran template`, `IEEE PDF eXpress` |
| 10 | [ieee-venue-selector](./skills/ieee-venue-selector/) | Beta | Curated 12 IEEE Transactions + 8 conference matrix; page-limit / blind / overlength-fee decision aid | `IEEE venue selection`, `IEEE journal recommendation` |

> Every sub-skill directory ships the same shape: `SKILL.md` + `README.md` + `references/` (IEEE official sources) + `tests/rubric.md` (6-dimension evaluation) + ≥ 3 fixture cases.

---

## 🚀 Why use this

- **Real IEEE spec** — every rule cites an IEEE Author Center / IEEE Editorial Style Manual / IEEEtran source; no "AI's idea of academic best practice"
- **Claude + Codex compatible** — SKILL.md uses the standard Agent Skills format; loads in both Claude Code and Codex CLI
- **10 skills that chain** — `ieee-venue-selector` → `ieee-writing` → `ieee-citation` → `ieee-figure` → `ieee-template` → `ieee-response`, full pipeline coverage
- **Quality gating** — each sub-skill has a 6-dimension `rubric.md` (Completeness / Traceability / Factuality / IEEE-fit / Actionability / Cross-skill integration); ≥24/30 to ship
- **No copying, no inventing** — structure inspired by nature-skills, but **all IEEE content authored independently**; every URL WebFetch-verified

---

## ⚡ Quick start

See [install.md](./install.md) for the three full installation paths (Codex direct / Claude Code subagent wrapper / manual copy).

---

## 🆚 Comparison

| Repo | Focus | Coverage |
|---|---|---|
| [Yuan1z0825/nature-skills](https://github.com/Yuan1z0825/nature-skills) | Nature-family biomed | 9 skills; writing + figures + citations, Nature style |
| [cookjohn/ieee-skills](https://github.com/cookjohn/ieee-skills) | IEEE Xplore browser automation | 9 skills; search / download / BibTeX export |
| **IEEE-suite-skills** (this repo) | **End-to-end IEEE manuscript pipeline** | **10 skills**; writing / citation / figures / LaTeX / response / data / venue |

All three can run side by side.

---

## 🗺️ Roadmap

- [ ] v0.1.0 — initial release of 10 sub-skills + awesome-claude-skills PR
- [ ] v0.2.0 — `ieee-cover-letter` + `ieee-orcid` + IEEE Access OA workflow
- [ ] v0.3.0 — integration path with [`cookjohn/ieee-skills`](https://github.com/cookjohn/ieee-skills): `ieee-academic-search` delegates Xplore automation to their tools

---

## 🤝 Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md). Conventional Commits. Self-rubric scoring required in PR description.

---

## 📜 License

[MIT](./LICENSE). IEEE official PDFs are referenced by URL only (© IEEE); `IEEEtran.cls` from CTAN ships under LPPL.

---

## 🙏 Credits

- [`Yuan1z0825/nature-skills`](https://github.com/Yuan1z0825/nature-skills) — engineering-structure inspiration
- [`cookjohn/ieee-skills`](https://github.com/cookjohn/ieee-skills) — complementary IEEE Xplore automation
- IEEE Author Center — the canonical authority every rule traces back to
