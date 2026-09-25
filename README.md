# attri-mcp

Everything for using [Attri](https://attri.io) from an AI assistant: the skills and plugin manifests that wrap Attri's MCP server. The server itself runs inside the Attri app at `https://app.attri.io/mcp`; this repo is what marketplaces list and what assistants read to use it well. Attri is link attribution, site analytics, Search Console data joined to on-site behaviour, and the posture review (ranked findings on what to fix first).

The assistant talks to Attri through the MCP server at `https://app.attri.io/mcp`. Sign-in is OAuth 2.1; you choose which workspaces the assistant may use and what it may do. Setup per client: <https://attri.io/docs/api/assistants>.

## Install

| Client | How |
|---|---|
| Claude Code | `claude plugin marketplace add attri-io/attri-mcp` then `claude plugin install attri@attri` |
| Grok Build / Grok Bot | Search "Attri" in the plugin marketplace, or point at this repo |
| Cursor | Search "Attri" in the plugin marketplace |
| Claude.ai, ChatGPT, anything with a custom-connector field | Add `https://app.attri.io/mcp` directly; no plugin needed |

Each client opens Attri in your browser the first time; you pick the workspaces and permissions there.

## Layout

| Path | What it is |
|---|---|
| `.mcp.json` / `mcp.json` | The MCP server declaration (Claude Code and Grok read the dotted file, Cursor the plain one) |
| `.claude-plugin/`, `.grok-plugin/`, `.cursor-plugin/` | Plugin manifests per client; same metadata |
| `skills/` | The skills below, loaded by every client |
| `templates/` | The Grok Bot template's instructions, routine and setup text |
| `assets/logo.svg` | The Attri mark |

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
