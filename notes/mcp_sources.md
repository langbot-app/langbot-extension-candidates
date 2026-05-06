# MCP Candidate Sources and Methodology

Last checked: 2026-05-06

## Methodology

- Read `QUALITY.md` first and treated quality as higher priority than reaching exactly 100 rows.
- Used a blended source strategy:
  - LobeHub MCP marketplace top listings for high-signal servers such as Playwright, Context7, Tavily, Firecrawl, AntV Chart, Figma Context, Browserbase, and Obsidian.
  - mcpservers.org official/featured listings for vendor-backed servers such as GitHub, Cloudflare, Supabase, Exa, Apify, Aiven, AWS Labs, Azure, Grafana, MiniMax, and others.
  - GitHub repository metadata via `gh api` for stable source URLs, author/org, license SPDX id, stars/forks/watchers, update date, primary language, and topics.
  - Official/vendor repositories when a registry page was unavailable but the repo had strong provenance and clear MCP utility.
- Wrote `data/processed/mcp_candidates.csv` with 89 rows. This intentionally stays below 100 rather than padding with low-provenance or novelty entries.
- `review_status=candidate` means the source looked useful and sufficiently reputable for a first import pass.
- `review_status=needs_review` means the candidate has clear utility/popularity but needs a stricter human/security review before publication, usually because of dual-use security capability, unclear license, social/private-data access, or high-power local automation.
- For license values, GitHub SPDX metadata was used when available. `unknown` is retained when GitHub reports no recognized license; the corresponding row includes a risk note requiring manual license verification.
- Runtime/install notes are intentionally concise importer hints based on language/package ecosystem and should be followed by README-level verification during implementation.

## Accepted source families

- **Official/vendor cloud and DevOps:** GitHub, Cloudflare, AWS Labs, Azure, Aiven, Grafana, Supabase, Terraform, Kubernetes, Docker-adjacent/container tooling.
- **Developer tooling:** Playwright, Chrome DevTools, JetBrains, XcodeBuildMCP, language-server MCPs, codebase memory/search, GitHub/Atlassian tooling.
- **Data and databases:** Qdrant, MongoDB, Bytebase DBHub, MySQL, Neon, Doris, Timescale/Postgres guidance, Financial Datasets.
- **Web/search/research:** Context7, Tavily, Exa, Firecrawl, Apify, Bright Data, Arxiv, paper search, NotebookLM, DuckDuckGo/open web search.
- **Productivity/knowledge:** Notion, Google Workspace, Slack, Obsidian, Contentful, Home Assistant.
- **Creative/media:** AntV charts, Figma Context, design extraction, shadcn UI, MiniMax, ElevenLabs, Excel, Unity/Unreal/Godot.
- **Security/reverse engineering:** HexStrike, IDA, Ghidra, JADX, WinDbg were retained as `needs_review` due to obvious dual-use value and risk.

## Rejected or intentionally omitted

These were considered but omitted from the final CSV because they did not meet the quality bar for this pass:

- **Duplicate/lower-signal alternatives:** `executeautomation/mcp-playwright`, `leonardsellem/n8n-mcp-server`, duplicate Kubernetes/MySQL variants, RedNote duplicates of Xiaohongshu-style integrations.
- **Boilerplates/templates/curricula rather than usable servers:** `iannuttall/mcp-boilerplate`, `microsoft/mcp-for-beginners`, generic SDK/framework-only repos where end-user utility was indirect.
- **Awesome lists/directories only:** Awesome MCP lists, MCP getting-started guides, marketplace indexes without direct server functionality.
- **Intentionally vulnerable or training targets:** `harishsg993010/damn-vulnerable-MCP-server` and similar security-lab projects; useful for education, not a marketplace integration.
- **Unclear/novelty or weak provenance from metadata alone:** small or ambiguous repositories where the README would need deeper validation before inclusion.
- **404/unverified repo candidates:** `docker/mcp-servers`, `Shopify/dev-mcp`, and `mcp-server-time/mcp-server-time` did not resolve through GitHub API during this pass, so they were omitted rather than guessed.
- **Potentially high-risk social automations without enough review:** some WhatsApp/RedNote/Xiaohongshu-style variants were omitted or kept only as `needs_review` when popularity was high enough.

## Follow-up recommendations

1. Before publishing any `candidate`, run a README/package-level verifier to confirm exact install command, transport type, environment variables, and whether tools can write externally.
2. For every `needs_review` row, require manual security review and scoped demo credentials before enabling in LangBot Space.
3. Add registry-specific fields later if the importer needs transport (`stdio`, `sse`, `streamable-http`) or package name separate from repository URL.
