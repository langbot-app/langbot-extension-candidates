# Quality Bar for LangBot Extension Candidates

This dataset is for the first LangBot Space Extension Market launch. Do not pad the list.

## Acceptance criteria

Every accepted row must have:

1. Clear utility for LangBot users, not merely a toy/demo.
2. A stable source URL and preferably an upstream repo/official docs page.
3. Author or organization identified.
4. License identified from source/repo metadata; if unknown, mark `unknown` and explain in `risk_notes`.
5. Popularity evidence where available: GitHub stars, downloads, registry ranking, official adoption, or LobeHub metrics.
6. A concise functional summary based on reading the source page/repo, not inferred from the name alone.
7. Useful tags for extension-market filtering.
8. Runtime/install notes sufficient for a later importer/sandbox evaluator.
9. Risk notes for auth requirements, secret handling, network/file-system access, abandoned repos, unclear license, or security-sensitive capabilities.

## Rejection / omit criteria

Omit or mark `needs_review` if:

- It is a duplicate, fork-only copy, or wrapper with no clear maintenance story.
- It is abandoned or has unclear provenance and no strong utility.
- It lacks enough public information to verify author/license/function.
- It is novelty-only and not useful for real LangBot scenarios.
- It requires unsafe privileges without obvious sandbox boundaries.

## Delivery rule

Prefer 70 genuinely high-quality candidates over 100 padded candidates during intermediate drafts. Final target remains 100 MCP + 100 Skills, but quality wins over count.
