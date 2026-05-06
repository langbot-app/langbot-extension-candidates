# MCP License/Metadata Research Notes — 2026-05-06

## Methodology

Second-pass enrichment started from `data/processed/mcp_candidates.csv` (100 rows). I reviewed the required quality/research guidance, then used the existing GitHub metadata fields from the first pass plus direct upstream source checks. Because unauthenticated GitHub core API quota was exhausted during the prior attempt, this pass used raw repository source where available (`README.md`, `package.json`, `pyproject.toml`, `LICENSE`, `LICENSE.md`, `COPYING` on `main`/`master`) and retained conservative status where rights remained unclear.

For each row, I normalized generic runtime notes where a README/package manifest exposed an install/launch hint, replaced generic risk placeholders with category-specific risk notes, and kept rows with unresolved license as `needs_review`.

## License fixes

- `unreal-mcp`: changed `unknown` → `MIT`; evidence: README badge and License section say MIT; no root LICENSE file found.
- `magic-mcp`: changed `unknown` → `ISC`; evidence: `package.json` has `license: ISC`; no root LICENSE file found.
- `apimatic-validator-mcp`: changed `unknown` → `ISC`; evidence: `package.json` has `license: ISC`; no root LICENSE file found.

## Still unresolved / conservative review

- `xiaohongshu-mcp`: remains `unknown` / `needs_review`. Checked GitHub metadata from first pass, README.md on main/master, LICENSE/LICENSE.md/COPYING on main/master, package/Go manifests and Docker documentation references; no explicit redistributable license found. High platform/account automation and ToS risk also warrants manual review.

## Validation

- CSV schema validated against 14 expected columns.
- Row count preserved: 100 MCP candidates.
- Unknown licenses after pass: 1 (`xiaohongshu-mcp`), conservatively marked `needs_review`.
- Rows with unresolved licenses are not marked `candidate`.

## Notes for importer follow-up

- Runtime commands extracted from README snippets/package manifests are intake hints, not execution validation. Before marketplace publication, run each candidate in a sandbox with scoped env vars and confirm exact stdio/SSE/HTTP transport.
- Rows involving SaaS accounts, browsers, local IDEs, databases, infrastructure, finance, mailbox/chat data, or dual-use security remain intentionally conservative in `risk_notes` even when marked `candidate`.
