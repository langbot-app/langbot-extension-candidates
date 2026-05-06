# Skill candidate sources and methodology

Last checked: 2026-05-06

## Scope

This file documents the `data/processed/skill_candidates.csv` review pass for LangBot Space Extension Market seed candidates. The CSV contains 100 Skill records using the existing shared schema and is focused on broadly useful agent skills that can plausibly be imported into a sandboxed Skill-compatible runtime.

## Sources used

- **LobeHub Skills marketplace** (`https://lobehub.com/skills` and individual `/skills/...` listing pages)
  - Used for candidate discovery, names, descriptions, listing URLs, categories/tags, install/rating/comment signals, and listing update dates where available.
- **GitHub repository metadata / upstream repositories**
  - Used to confirm repository URLs, author/owner, visible license metadata where available, and coarse popularity signals such as stars/forks.
- **Official or upstream project docs/repositories linked from the listings**
  - Used as corroboration for runtime/install expectations and risk notes where the listing alone was insufficient.

## Review method

1. Started from LobeHub Skill listings and prioritized high-utility/general-purpose entries: document processing, web/browser automation, search/research, coding/dev tools, media generation, memory, productivity, and design/content generation.
2. Excluded obviously narrow, duplicate, or risky entries when better general alternatives were available.
3. For each selected entry, recorded:
   - `source_url`: the LobeHub listing page used for discovery/review.
   - `repo_url`: upstream repository shown or corroborated from the listing.
   - `license`: upstream license when clearly available; otherwise `unknown`.
   - `popularity`: marketplace installs/ratings/comments plus GitHub stars/forks when available.
   - `runtime_or_install`: concise import/install expectation and notable runtime needs.
   - `risk_notes`: licensing, secrets, browser/account access, local file access, outbound network, and marketplace-review concerns.
4. Marked entries as:
   - `candidate` when license/source looked usable and risks were ordinary for sandboxed import.
   - `needs_review` when license was unknown/proprietary or the skill touches sensitive surfaces such as credentials, browser sessions, social/account actions, infrastructure, or local files.

## Important caveats

- Many LobeHub entries do **not** expose a clear redistributable license in the registry metadata. These are intentionally marked `needs_review` with license risk notes rather than guessed.
- Popularity metrics are human-readable snapshots from the review date and should be refreshed before a public launch.
- This is a market-seeding shortlist, not a final approval list. Before publishing/importing any skill, run a functional sandbox test and a source/license review.
- External API skills should use scoped secrets and explicit confirmation gates for writes or account-affecting actions.
