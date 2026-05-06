# LangBot Extension Candidates

Candidate MCP servers and Skills for LangBot Space's Extension Market.

## Outputs

- `data/processed/mcp_candidates.csv` — target: 100 reviewed MCP candidates
- `data/processed/skill_candidates.csv` — target: 100 reviewed Skills candidates

## Schema

Common columns:

- `type`: `mcp` or `skill`
- `name`
- `summary`
- `author`
- `source_url`
- `repo_url`
- `license`
- `popularity`: human-readable popularity metrics, e.g. GitHub stars/downloads/LobeHub stats
- `tags`: semicolon-separated category tags
- `runtime_or_install`
- `risk_notes`
- `review_status`: `candidate`, `needs_review`, `rejected`
- `source_registry`
- `last_checked`

## Notes

Created for Rock / LangBot extension-market launch prep.
