# Skill candidate license research — second pass

Date: 2026-05-06
Dataset: `data/processed/skill_candidates.csv` (100 rows)

## Methodology

- Read `LICENSE_RESEARCH.md` and `QUALITY.md` acceptance/review rules.
- For all 100 LobeHub skill rows, fetched the LobeHub markdown pages and checked identifier, author, install/rating/license fields, and GitHub cards.
- For each unique GitHub repo in `repo_url`, queried GitHub repository metadata/license information with authenticated `gh api` when possible and shallow-cloned public repos for source-tree checks.
- Checked root `LICENSE*`, per-skill `LICENSE.txt`, `SKILL.md` frontmatter, README install instructions, and package metadata (`package.json`) where repo-level metadata was missing or misleading.
- Updated `license`, `popularity`, `runtime_or_install`, `risk_notes`, `review_status`, `source_registry`, and `last_checked` conservatively.
- Rule applied: unresolved license or unclear redistribution rights => `needs_review`; permissive licenses with usable source trail => `candidate` unless source provenance was not verifiable.

## Validation summary

- CSV schema preserved: `type,name,summary,author,source_url,repo_url,license,popularity,tags,runtime_or_install,risk_notes,review_status,source_registry,last_checked`
- Row count preserved: 100 rows.
- License distribution after enrichment:
  - MIT: 67
  - unknown: 16
  - Apache-2.0: 7
  - Proprietary: 2
  - Proprietary. LICENSE.txt has complete terms: 2
  - ISC: 2
  - WTFPL: 2
  - Sustainable Use License 1.0: 1
  - BSD-3-Clause: 1
- Review status after enrichment:
  - `candidate`: 77
  - `needs_review`: 23

## Notable resolutions

- Many repo-level unknown rows were resolved from root GitHub licenses:
  - `openclaw/openclaw`, `MiniMax-AI/skills`, `garrytan/gstack`, `kepano/obsidian-skills`, `browser-use/browser-use`, `bytedance/deer-flow`, `brave/brave-search-skills`, `tavily-ai/skills`, `exa-labs/exa-mcp-server`, etc. now use their SPDX license.
- MiniMax rows were normalized: most root/per-skill MIT; `ppt-editing-skill` and `ppt-orchestra-skill` remain proprietary/source-available because their own frontmatter says so.
- Anthropic document skills (`pptx`, `pdf`) remain proprietary; `canvas-design` is Apache-2.0 from its own `LICENSE.txt`.
- Firecrawl rows are `ISC` from `package.json` because repo-level GitHub license API did not expose a root license file.
- Binance `trading-signal` is `MIT` from skill frontmatter even though the repo root lacked a detected license.
- `frontend-ui-ux` is not open-source: root `LICENSE.md` is Sustainable Use License 1.0 with non-commercial/commercial-use restrictions; kept `needs_review`.

## Unresolved / needs-review items

These rows intentionally remain `needs_review` with detailed evidence in `risk_notes`:

1. `skill-vetter` — `openclaw/skills` source repo could not be verified; LobeHub license blank.
2. `capability-evolver` — `openclaw/skills` source repo could not be verified; LobeHub license blank.
3. `proactive-agent` — `openclaw/skills` source repo could not be verified; LobeHub license blank.
4. `pptx` — proprietary Anthropic document skill terms restrict redistribution.
5. `self-improvement` — `openclaw/skills` source repo could not be verified; LobeHub license blank.
6. `pdf` — proprietary Anthropic document skill terms restrict redistribution.
7. `frontend-ui-ux` — Sustainable Use License 1.0 is non-OSI/restricted.
8. `memory` — `openclaw/skills` source repo could not be verified; LobeHub license blank.
9. `prompt-guard` — `openclaw/skills` source repo could not be verified; LobeHub license blank.
10. `reddit` — `openclaw/skills` source repo could not be verified; LobeHub license blank.
11. `memory-hygiene` — `openclaw/skills` source repo could not be verified; LobeHub license blank.
12. `baoyu-image-gen` — checked repo root, README/package metadata, and matching `SKILL.md`; no explicit redistributable license found.
13. `baoyu-slide-deck` — same JimLiu no-license evidence.
14. `scrapling-official` — LobeHub reports BSD-3-Clause, but `openclaw/skills` source repo could not be verified; source trail remains weak.
15. `ppt-editing-skill` — proprietary MiniMax plugin skill.
16. `ppt-orchestra-skill` — proprietary MiniMax plugin skill.
17. `slides` — LobeHub reports Apache-2.0, but the current `openai/skills` clone did not expose a matching `slides` skill path; confirm upstream path before publishing.
18. `baoyu-infographic` — same JimLiu no-license evidence.
19. `google-flights-search` — `openclaw/skills` source repo could not be verified; LobeHub license blank.
20. `baoyu-xhs-images` — same JimLiu no-license evidence.
21. `follow-builders` — checked GitHub API, repo root, README/package metadata, and matching `SKILL.md`; no explicit redistributable license found.
22. `baoyu-article-illustrator` — same JimLiu no-license evidence.
23. `codebase-to-course` — checked GitHub API, repo root, README/package metadata, and matching `SKILL.md`; no explicit redistributable license found.

## Follow-up recommendations

- Replace or fix rows pointing at `https://github.com/openclaw/skills` if there is a current public source repository; right now those entries rely mainly on LobeHub pages.
- Ask JimLiu and Zara Zhang repos for explicit LICENSE files before market inclusion.
- Re-check `openai-skills-slides` against LobeHub/upstream because the current public repo tree did not contain a `slides` skill path.
- Keep proprietary Anthropic/MiniMax document skills out of redistributable marketplace packaging unless legal approves the exact terms.
