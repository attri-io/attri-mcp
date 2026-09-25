# attri-mcp

Everything for using [Attri](https://attri.io) from an AI assistant: the skills and plugin manifests that wrap Attri's MCP server. The server itself runs inside the Attri app at `https://app.attri.io/mcp`; this repo is what marketplaces list and what assistants read to use it well. Attri is link attribution, site analytics, Search Console data joined to on-site behaviour, and the posture review (ranked findings on what to fix first).

The assistant talks to Attri through the MCP server at `https://app.attri.io/mcp`. Sign-in is OAuth 2.1; you choose which workspaces the assistant may use and what it may do. Setup per client: <https://attri.io/docs/api/assistants>.

## Contents

| Path | What it is |
|---|---|
| `skills/attri-search-analyst/SKILL.md` | How to read Attri's findings and search data, what "could move" means, and the order to work in |
| `skills/attri-weekly-review/SKILL.md` | A weekly routine: what moved, what to do next, plan it |

Plugin manifests for Grok Build / Grok Bot and Cursor, and the Claude Code plugin, live alongside these skills (see `specs/assistant-integrations.md` in the product repo for the plan).

## Tools the skills rely on

Read: `list_workspaces`, `get_workspace`, `get_site_overview`, `list_top_pages`, `list_sources`, `list_outbound_clicks`, `get_search_overview`, `list_search_queries`, `list_search_pages`, `get_search_query_pages`, `list_findings`, `get_finding`, `list_links`, `list_top_links`, `list_conversions`, `list_goals`.
Write (need the matching scope): `create_link`, `set_finding_status`.

## License

MIT for the contents of this repository. Attri itself is a commercial product.
