# XLAB Claude Code Team Config

Shared Claude Code setup for the XLAB team. Clone this repo, follow the setup below, and you get working Notion + MS365 integrations.

## Prerequisites

- [Claude Code CLI](https://docs.anthropic.com/en/docs/claude-code/overview) installed (`npm i -g @anthropic-ai/claude-code`)
- Node.js 18+
- Notion API token (get from https://www.notion.so/profile/integrations)
- MS365 account with XLAB tenant access

## Setup (5 min)

### 1. Clone this repo

```bash
git clone https://github.com/jtrjtrjtr/claude-team-config.git
cd claude-team-config
```

### 2. Register MCP servers

**Notion** (read/write access to shared Notion workspace):

```bash
claude mcp add notion-query \
  -s user \
  -e NOTION_API_TOKEN=your_token_here \
  -- npx -y @suekou/mcp-notion-server
```

**MS365** (Outlook, Calendar, Teams, OneDrive):

```bash
claude mcp add ms-365 \
  -s user \
  -- npx -y @softeria/ms-365-mcp-server \
  --org-mode \
  --tenant-id 49a87d3c-f1c5-4db3-b174-d456cce60b3d \
  --client-id 084a3e9f-a9f4-43f7-89f9-d229cf97853e
```

Then login:

```bash
claude
# Inside Claude Code, type:
# "login to MS365"
# Follow the device code flow in browser
```

### 3. Verify

```bash
claude
# Try: "List my recent emails" or "Search Notion for XLAB"
```

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
