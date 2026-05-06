# XLAB Claude Code Team Config

Shared Claude Code setup for the XLAB team. Clone this repo, follow the setup below, and you get working integrations (Notion, MS365) and all XLAB skills.

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
git clone --recurse-submodules https://github.com/jtrjtrjtr/claude-team-config.git
cd claude-team-config
```

> If you already cloned without `--recurse-submodules`, run:
> `git submodule update --init --recursive`

### 2. Connect cloud integrations

Open Claude Code in this repo directory and connect these integrations. All are **cloud-based** (built into claude.ai) — no local npm packages needed.

#### Notion

1. In Claude Code, type: `connect to Notion` (or use the integrations menu)
2. Authorize with your Notion account that has access to XLAB workspace
3. Grant access to the pages/databases you need

#### Microsoft 365 (Outlook, Calendar, Teams, OneDrive, SharePoint)

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

If you prefer local MCP servers instead of cloud integrations (e.g. for offline use or advanced config):

<details>
<summary>Local Notion MCP (with database query filters)</summary>

```bash
claude mcp add notion-query \
  -s user \
  -e NOTION_API_TOKEN=your_token_here \
  -- npx -y @suekou/mcp-notion-server
```

Get your token from https://www.notion.so/profile/integrations

Advantage over cloud integration: supports `notion_query_database` with property filters.
</details>

<details>
<summary>Local MS365 MCP (100+ tools, full read/write)</summary>

```bash
claude mcp add ms-365 \
  -s user \
  -- npx -y @softeria/ms-365-mcp-server \
  --org-mode \
  --tenant-id 49a87d3c-f1c5-4db3-b174-d456cce60b3d \
  --client-id 084a3e9f-a9f4-43f7-89f9-d229cf97853e
```

Then inside Claude Code: `login to MS365` and follow the device code flow.

Advantage over cloud integration: 100+ tools (vs 6 read-only), includes write operations.
</details>

## XLAB Skills

This repo includes all XLAB skills — auto-loaded by Claude Code from `.claude/skills/`:

| Skill | Purpose |
|-------|---------|
| **xlab-brand** | Brand identity — colors, typography, logo rules, visual guidelines |
| **xlab-content** | Brand voice, tone rules, product portfolio descriptions (CZ/EN) |
| **xlab-events** | Event production — dramaturgy, proposals, engagement architecture |
| **xlab-pricing** | Central pricing, cost calculations, quote generation |
| **xlab-proposal** | Client proposals — structure, formatting, shell documents |
| **xlab-social** | Social media — Instagram and LinkedIn guides |
| **xlab-pptx-template** | PowerPoint generation with XLAB template |

Skills are sourced from [XLAB_OFFICE_AUTOMATION](https://github.com/jtrjtrjtr/XLAB_OFFICE_AUTOMATION) (git submodule).

### Using skills on claude.ai (without Claude Code)

If your colleague uses claude.ai web (not Claude Code):
1. Go to the skill file on GitHub: `skills/xlab-office/skills/<name>/SKILL.md`
2. Copy the content
3. In claude.ai, create a Project "XLAB" and paste it into Project Instructions
4. Work inside that project for XLAB tasks, personal chats outside

### Updating skills

```bash
git submodule update --remote
git add skills/xlab-office
git commit -m "Update XLAB skills to latest"
git push
```

## File structure

```
CLAUDE.md                        # Shared agent instructions
CLAUDE.local.md                  # Your personal overrides (gitignored)
.claude/
  settings.json                  # Shared permission rules
  settings.local.json            # Your personal permissions (gitignored)
  skills/                        # Auto-loaded by Claude Code
    xlab-brand/                  # -> symlink to submodule
    xlab-content/                # -> symlink to submodule
    xlab-events/                 # extracted from .skill ZIP
    xlab-pricing/                # -> symlink to submodule
    xlab-proposal/               # -> symlink to submodule
    xlab-social/                 # extracted from .skill ZIP
    xlab-pptx-template/          # -> symlink to submodule
skills/
  xlab-office/                   # Git submodule -> XLAB_OFFICE_AUTOMATION
  cowork/                        # Cowork skills (coming soon)
```

## Personal overrides

Create `CLAUDE.local.md` for instructions specific to you (your name, role, preferences). It will not be committed.

## Security

- **Never** commit API tokens or credentials to this repo
- Each user has their own Notion token + their own MS365 login
- Local overrides: `.claude/settings.local.json` (gitignored)

## Moving to XLAB org

When the XLAB GitHub org is ready, the repo owner can transfer it:

```bash
gh repo transfer jtrjtrjtr/claude-team-config XLAB-org-name
```
