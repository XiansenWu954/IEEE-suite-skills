# Installation guide

`IEEE-suite-skills` ships 10 sub-skills, each in its own `skills/ieee-*/` folder.
You can install all 10, just the ones you need, or chain them via subagent wrappers.
Three paths below. Pick whichever matches your runtime.

---

## Path 1 — Codex CLI direct (recommended for Codex users)

Codex CLI looks for skills under `~/.codex/skills/`. Drop the folder there.

```bash
# 1. Clone the repo
git clone https://github.com/XiansenWu954/IEEE-suite-skills.git
cd IEEE-suite-skills

# 2. Make sure the Codex skills dir exists
mkdir -p ~/.codex/skills

# 3a. Install a single sub-skill
cp -R skills/ieee-writing ~/.codex/skills/

# 3b. Or install all 10
for d in skills/ieee-*; do cp -R "$d" ~/.codex/skills/; done

# 4. Confirm
ls ~/.codex/skills/ | grep ieee-
```

After install, in a Codex session: refer to the skill by name (`ieee-writing`, etc.).

---

## Path 2 — Claude Code subagent wrapper

Claude Code (`claude` CLI) loads agents from `~/.claude/agents/`. The agent file
is a tiny `.md` with frontmatter that defers to the actual `SKILL.md` body.

```bash
# 1. Clone to a stable location
git clone https://github.com/XiansenWu954/IEEE-suite-skills.git ~/ai-skills/IEEE-suite-skills

# 2. Create one agent wrapper per skill you want
mkdir -p ~/.claude/agents

cat > ~/.claude/agents/ieee-writing.md <<'EOF'
---
name: ieee-writing
description: Author IEEE journal manuscripts following the IEEE Editorial Style Manual: §I-§VI structure, ≤250-word abstract, 5-8 keywords, numeric `[N]` references, single-blind defaults.
---
First read ~/ai-skills/IEEE-suite-skills/skills/ieee-writing/SKILL.md, then follow its workflow.
EOF

cat > ~/.claude/agents/ieee-citation.md <<'EOF'
---
name: ieee-citation
description: Produce IEEEtran-conforming BibTeX entries with `[N]` numeric citation handling.
---
First read ~/ai-skills/IEEE-suite-skills/skills/ieee-citation/SKILL.md, then follow its workflow.
EOF

# ... repeat for any of the 10 skills you want
```

Or batch-create wrappers for all 10:

```bash
for skill in ~/ai-skills/IEEE-suite-skills/skills/ieee-*; do
  name=$(basename "$skill")
  desc=$(awk '/^description:/{sub(/^description: /,""); print; exit}' "$skill/SKILL.md")
  cat > ~/.claude/agents/$name.md <<EOF
---
name: $name
description: $desc
---
First read $skill/SKILL.md, then follow its workflow.
EOF
done
```

Confirm:

```bash
ls ~/.claude/agents/ | grep ieee-
```

In a Claude Code session, the skills become invokable by name.

---

## Path 3 — Project-level (per-repo `.claude/skills/`)

Use this if you want IEEE-suite-skills scoped to one project rather than your
whole user. Drop the folders into the project's `.claude/skills/`:

```bash
cd /path/to/your-paper-project
mkdir -p .claude/skills

git clone https://github.com/XiansenWu954/IEEE-suite-skills.git /tmp/iss
cp -R /tmp/iss/skills/ieee-writing .claude/skills/
cp -R /tmp/iss/skills/ieee-citation .claude/skills/
# ... etc

# Optional: track which version of IEEE-suite-skills you have
echo "Vendored from IEEE-suite-skills@$(cd /tmp/iss && git rev-parse --short HEAD)" \
  > .claude/skills/IEEE-suite-skills.VERSION
```

This keeps the project's IEEE skill set frozen-in-time and shippable with the
project repo if you commit `.claude/skills/`.

---

## Plugin marketplace (when published)

If your runtime supports Codex plugin marketplaces:

```bash
# Codex marketplace (when listed)
codex plugin install IEEE-suite-skills
```

The plugin manifest lives at [`plugins/ieee-suite-skills/.codex-plugin/plugin.json`](./plugins/ieee-suite-skills/.codex-plugin/plugin.json).

---

## Verifying install

After any path, ask Claude / Codex to invoke a sub-skill:

```
Use the ieee-writing skill to draft the abstract section for an IEEE
Transactions on Mobile Computing manuscript on <your topic>.
```

You should see the assistant load IEEE-spec constraints (≤250 words, 5-8 keywords,
single-blind defaults) without you having to remind it.

---

## Updating

Re-pull and re-copy:

```bash
cd ~/ai-skills/IEEE-suite-skills && git pull origin main
# Re-run your install command (whichever path you used)
```

Or in the project-level path, re-vendor and update the `.VERSION` stamp.

---

## Troubleshooting

- **"Skill not found"**: confirm the folder under `~/.codex/skills/` or `~/.claude/agents/`
  matches the skill name exactly. The folder name must match `SKILL.md` `name:` field.
- **URL fetch failures inside a skill**: IEEE occasionally moves docs.
  See `.github/workflows/check-links.yml` for the dead-link check; open an
  issue if you find one.
- **License questions**: `LICENSE` (MIT) covers our content. IEEE PDFs are
  URL-only references. `IEEEtran.cls` (in `skills/ieee-template/references/`)
  ships under LPPL.

---

## Optional: install alongside complementary repos

```bash
# IEEE manuscript layer (this repo)
git clone https://github.com/XiansenWu954/IEEE-suite-skills.git ~/ai-skills/IEEE-suite-skills

# IEEE Xplore browser automation (complementary)
git clone https://github.com/cookjohn/ieee-skills.git ~/ai-skills/ieee-xplore-skills

# Then install whichever skills you want from each
```

The two repos use different folder prefixes (`ieee-*` for ours, also `ieee-*` for cookjohn's
but different skill names like `ieee-search`, `ieee-export`) and don't collide. Both can
coexist in `~/.codex/skills/`.
