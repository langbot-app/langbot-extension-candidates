# MCP candidate sources and methodology

Last checked: 2026-05-06

## Sources consulted

- LobeHub MCP marketplace: `https://lobehub.com/mcp`
  - Used as a marketplace sanity-check source. The page is heavily client-rendered in the lightweight fetcher, so it was not used as the primary structured data source.
- Official MCP Registry: `https://registry.modelcontextprotocol.io/v0/servers`
  - Queried to confirm there is an active official registry and to compare registry metadata shape: server name, description, packages/remotes, repository, published/updated metadata.
- Official MCP reference server README: `https://github.com/modelcontextprotocol/servers`
  - Used to understand reference-server status and security cautions; reference examples are educational and should not be assumed production-ready.
- GitHub repository search/topic metadata:
  - `https://github.com/topics/mcp-server`
  - Authenticated GitHub API searches for `topic:mcp-server`, `"MCP server"`, and `"Model Context Protocol server"`.

## Selection approach

1. Collected repository metadata from GitHub search results across MCP-server topics and explicit MCP-server search phrases.
2. Kept repositories whose name or description explicitly identifies them as an MCP server or service-specific MCP implementation.
3. Excluded obvious non-market candidates such as awesome lists, SDKs/framework-only repos, client apps, tutorials, guides, registries/directories, boilerplates, and intentionally vulnerable demo servers.
4. Sorted candidates by GitHub stars as a rough popularity signal, then kept 110 rows so the file exceeds the 100-row target.
5. For each row, recorded the GitHub description, owner, repository URL, SPDX license metadata when available, stars/forks/watchers/update date, GitHub topics, primary language, and a best-effort install/runtime hint based on root repository files (`package.json`, `pyproject.toml`, `go.mod`, `Cargo.toml`, Docker files, etc.).

## Review caveats

- This is a metadata-level market screening, not a source-code security audit.
- `review_status=candidate` means the candidate looks plausible for marketplace review from public metadata. It does **not** mean approved for production.
- `review_status=needs_review` is used when license metadata is missing/ambiguous or the summary is weak.
- Before publishing any extension, manually inspect README install instructions, package provenance, license terms, maintenance activity, required secrets/OAuth scopes, network/file-system permissions, and whether the server is local or remote-hosted.
- Some high-star projects are broad products with MCP-server support rather than narrow one-purpose servers; they are retained only when public metadata explicitly describes MCP-server functionality.
