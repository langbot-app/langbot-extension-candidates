# License and Metadata Research Pass

Goal: convert the first-pass candidate list into review-ready marketplace intake data.

For every row, try to verify:

1. SPDX license from GitHub API, repo `LICENSE*`, package metadata, official docs, or registry page.
2. Author/maintainer organization from upstream source, not inferred only from slug.
3. Popularity evidence with date: GitHub stars/forks/update time, registry installs, LobeHub installs/ratings/comments, downloads, or official adoption.
4. Runtime/install command or integration notes from README/package docs.
5. Risk notes covering credentials, OAuth scopes, filesystem/network/browser/database access, write/destructive operations, maintenance, and redistribution risk.
6. Source trail in notes if license remains unknown: e.g. `checked GitHub API, repo root, LICENSE file, package metadata, LobeHub page; no explicit redistributable license found`.

Do not mark a row `candidate` if the license is unresolved or redistribution rights are unclear; keep it `needs_review` with specific evidence.
