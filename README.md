# XLAB Claude Code Team Config

Shared Claude Code setup for the XLAB team. Clone this repo, follow the setup below, and you get working integrations with Notion, MS365, Google Drive, Calendar and Gmail.

## Prerequisites

- Claude Code — any of these:
  - **CLI**: `npm i -g @anthropic-ai/claude-code` (needs Node.js 18+)
  - **Desktop app**: [Mac](https://claude.ai/download) / Windows
  - **Web**: [claude.ai/code](https://claude.ai/code) (Pro/Max/Team plan)
- XLAB MS365 account (your @xlab.cz or @xlabrealtime.com login)
- Anthropic account (Pro, Max or Team plan)

## Setup (5 min)

### 1. Clone this repo

```bash
git clone https://github.com/jtrjtrjtr/claude-team-config.git
cd claude-team-config
```

### 2. Connect cloud integrations

Open Claude Code in this repo directory and connect these integrations. All are **cloud-based** (built into claude.ai) — no local npm packages needed.

#### Notion

1. In Claude Code, type: `connect to Notion` (or use the integrations menu)
2. Authorize with your Notion account that has access to XLAB workspace
3. Grant access to the pages/databases you need

#### Microsoft 365 (Outlook, Calendar, Teams, OneDrive)

1. In Claude Code, type: `connect to Microsoft 365`
2. Login with your XLAB account (@xlab.cz or @xlabrealtime.com)
3. Tenant ID (for reference): `49a87d3c-f1c5-4db3-b174-d456cce60b3d`

#### Google Drive / Calendar / Gmail (optional)

1. In Claude Code, type: `connect to Google Drive` / `connect to Google Calendar` / `connect to Gmail`
2. Authorize with your Google account
3. Each service authenticates separately

### 3. Verify

```
Search Notion for XLAB
List my recent emails
What's on my calendar this week?
```

If any integration shows an auth error, reconnect it (step 2).

### Alternative: Local MCP servers

If you prefer local MCP servers instead of cloud integrations (e.g. for offline use or custom config):

<details>
<summary>Local Notion MCP</summary>

```bash
claude mcp add notion-query \
  -s user \
  -e NOTION_API_TOKEN=your_token_here \
  -- npx -y @suekou/mcp-notion-server
```

Get your token from https://www.notion.so/profile/integrations
</details>

<details>
<summary>Local MS365 MCP</summary>

```bash
claude mcp add ms-365 \
  -s user \
  -- npx -y @softeria/ms-365-mcp-server \
  --org-mode \
  --tenant-id 49a87d3c-f1c5-4db3-b174-d456cce60b3d \
  --client-id 084a3e9f-a9f4-43f7-89f9-d229cf97853e
```

Then inside Claude Code: `login to MS365` and follow the device code flow.
</details>

## File structure

```
CLAUDE.md                  # Shared agent instructions (everyone gets these)
CLAUDE.local.md            # Your personal overrides (gitignored)
.claude/
  settings.json            # Shared permission rules
  settings.local.json      # Your personal permissions (gitignored)
skills/                    # Shared skills (slash commands)
  cowork/                  # Cowork-related skills
```

## Personal overrides

Create `CLAUDE.local.md` for instructions specific to you (your name, role, preferences). It will not be committed.

## Adding skills

Put skill YAML files in `skills/`. See [Claude Code docs](https://docs.anthropic.com/en/docs/claude-code/skills) for the format.

## Moving to XLAB org

When the XLAB GitHub org is ready, the repo owner can transfer it:

```bash
gh repo transfer jtrjtrjtr/claude-team-config XLAB-org-name
```
