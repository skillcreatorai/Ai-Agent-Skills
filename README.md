<h1 align="center">
  <br>
  🔧 AI Agent Skills
  <br>
</h1>

<p align="center">
  <strong>Homebrew for AI agent skills.</strong><br>
  One command. Ten agents. Skills that follow you.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/skills-39-blue?style=flat-square" alt="Skills" />
  <img src="https://img.shields.io/badge/agents-10+-green?style=flat-square" alt="Compatible Agents" />
  <img src="https://img.shields.io/badge/license-MIT-brightgreen?style=flat-square" alt="License" />
  <img src="https://img.shields.io/npm/v/ai-agent-skills?style=flat-square&color=red" alt="npm" />
  <img src="https://img.shields.io/npm/dt/ai-agent-skills?style=flat-square&color=orange" alt="Downloads" />
</p>

<p align="center">
  <a href="https://skillcreator.ai/explore"><strong>Browse Skills</strong></a> ·
  <a href="https://skillcreator.ai/build"><strong>Create Skills</strong></a> ·
  <a href="https://agentskills.io"><strong>Specification</strong></a> ·
  <a href="https://x.com/skillcreatorai"><strong>Follow Updates</strong></a>
</p>

---

## Quick Start

```bash
# Browse skills interactively
npx ai-agent-skills browse

# Install from our curated catalog
npx ai-agent-skills install frontend-design

# Install for specific agents
npx ai-agent-skills install frontend-design --agent cursor
npx ai-agent-skills install frontend-design --agent codex
npx ai-agent-skills install frontend-design --agent amp

# Install from any GitHub repo
npx ai-agent-skills install anthropics/skills
npx ai-agent-skills install anthropics/skills/pdf    # specific skill

# Install from local path
npx ai-agent-skills install ./my-custom-skill
```

That's it. The skill installs to the right location for your agent automatically.

## Why This Exists

Every major AI coding agent now supports skills. But they're scattered everywhere.

This repo curates the best in one place. Quality over quantity. All skills follow the [Agent Skills spec](https://agentskills.io).

## Compatible Agents

Works with **Claude Code**, **Cursor**, **Amp**, **VS Code**, **GitHub Copilot**, **Goose**, **Letta**, **OpenCode**, and **Claude.ai**.

## Available Skills

### Development
| Skill | Description |
|-------|-------------|
| `frontend-design` | Production-grade UI components and styling |
| `mcp-builder` | Create MCP servers for agent tool integrations |
| `skill-creator` | Guide for creating new agent skills |
| `code-review` | Automated PR review patterns |
| `code-refactoring` | Systematic code improvement techniques |
| `backend-development` | APIs, databases, server architecture |
| `python-development` | Modern Python 3.12+ patterns |
| `javascript-typescript` | ES6+, Node, React, TypeScript |
| `webapp-testing` | Browser automation and testing with Playwright |
| `database-design` | Schema design and optimization |
| `llm-application-dev` | Build LLM-powered applications |
| `artifacts-builder` | Interactive React/Tailwind web components |
| `changelog-generator` | Generate changelogs from git commits |

### Documents
| Skill | Description |
|-------|-------------|
| `pdf` | Extract, create, merge, split PDFs |
| `xlsx` | Excel creation, formulas, data analysis |
| `docx` | Word documents with formatting |
| `pptx` | PowerPoint presentations |

### Creative
| Skill | Description |
|-------|-------------|
| `canvas-design` | Visual art and poster creation |
| `algorithmic-art` | Generative art with p5.js |
| `image-enhancer` | Improve image quality and resolution |
| `slack-gif-creator` | Create animated GIFs for Slack |
| `theme-factory` | Professional font and color themes |
| `video-downloader` | Download videos from various platforms |

### Business
| Skill | Description |
|-------|-------------|
| `brand-guidelines` | Apply brand colors and typography |
| `internal-comms` | Status updates and team communication |
| `competitive-ads-extractor` | Analyze competitor ad strategies |
| `domain-name-brainstormer` | Generate and check domain availability |
| `lead-research-assistant` | Identify and qualify leads |

### Productivity
| Skill | Description |
|-------|-------------|
| `doc-coauthoring` | Co-author docs, proposals, specs with structured workflow |
| `job-application` | Cover letters and applications using your CV |
| `qa-regression` | Automated regression testing with Playwright |
| `jira-issues` | Create, update, search Jira issues |
| `code-documentation` | Generate docs from code |
| `content-research-writer` | Research and write content with citations |
| `developer-growth-analysis` | Track developer growth metrics |
| `file-organizer` | Organize files and find duplicates |
| `invoice-organizer` | Organize invoices for tax prep |
| `meeting-insights-analyzer` | Analyze meeting transcripts |
| `raffle-winner-picker` | Randomly select contest winners |

## Commands

```bash
# Interactive browser (TUI)
npx ai-agent-skills browse

# List all available skills
npx ai-agent-skills list
npx ai-agent-skills list --category development
npx ai-agent-skills list --installed --agent cursor

# Install from catalog, GitHub, or local path
npx ai-agent-skills install <name>                    # from catalog
npx ai-agent-skills install <owner/repo>              # from GitHub
npx ai-agent-skills install <owner/repo/skill>        # specific skill from GitHub
npx ai-agent-skills install ./path                    # from local path
npx ai-agent-skills install <name> --agent cursor     # for specific agent
npx ai-agent-skills install <name> --dry-run          # preview only

# Manage installed skills
npx ai-agent-skills uninstall <name>
npx ai-agent-skills update <name>
npx ai-agent-skills update --all

# Discovery
npx ai-agent-skills search <query>
npx ai-agent-skills info <name>

# Configuration
npx ai-agent-skills config --default-agent cursor
```

### Supported Agents

| Agent | Flag | Install Location |
|-------|------|------------------|
| Claude Code | `--agent claude` (default) | `~/.claude/skills/` |
| Cursor | `--agent cursor` | `.cursor/skills/` |
| Amp | `--agent amp` | `~/.amp/skills/` |
| VS Code / Copilot | `--agent vscode` | `.github/skills/` |
| Goose | `--agent goose` | `~/.config/goose/skills/` |
| OpenCode | `--agent opencode` | `~/.opencode/skills/` |
| Codex | `--agent codex` | `~/.codex/skills/` |
| Letta | `--agent letta` | `~/.letta/skills/` |
| Portable | `--agent project` | `.skills/` (works with any agent) |

## Manual Install

```bash
# Clone the repo
git clone https://github.com/skillcreatorai/Ai-Agent-Skills.git

# Copy a skill to your skills directory
cp -r Ai-Agent-Skills/skills/pdf ~/.claude/skills/
```

## Create Your Own

Two options:

1. **Generate in 30 seconds**: [skillcreator.ai/build](https://skillcreator.ai/build)
2. **Build manually**: Follow the [Agent Skills spec](https://agentskills.io/specification)

## What Are Agent Skills?

An [open standard from Anthropic](https://agentskills.io) for extending AI agents. A skill is just a folder:

```
my-skill/
├── SKILL.md       # Instructions + metadata
├── scripts/       # Optional code
└── references/    # Optional docs
```

All major AI coding tools support this format.

## Contributing

1. Fork this repo
2. Add your skill to `/skills/<name>/`
3. Ensure `SKILL.md` follows the [spec](https://agentskills.io/specification)
4. Update `skills.json`
5. Submit PR

We review all contributions for quality and spec compliance.

## Links

- [Awesome Agent Skills](https://github.com/skillcreatorai/Awesome-Agent-Skills) - Curated list of 50+ skills
- [Agent Skills Spec](https://agentskills.io) - Official format documentation
- [Browse Skills](https://skillcreator.ai/discover) - Visual skill gallery with one-click install
- [Create Skills](https://skillcreator.ai/build) - Generate skills from plain English
- [Anthropic Skills](https://github.com/anthropics/skills) - Official example skills

## See Also

**[openskills](https://github.com/numman-ali/openskills)** - Requires global install, AGENTS.md sync, and Bash calls. Great for flexibility.

**ai-agent-skills** - Just `npx`, installs to native agent folders. Homebrew for skills.

---

## Credits & Attribution

This repository builds upon and curates skills from the open-source community:

- **[Anthropic Skills](https://github.com/anthropics/skills)** - Official example skills from Anthropic that established the Agent Skills specification
- **[ComposioHQ Awesome Claude Skills](https://github.com/ComposioHQ/awesome-claude-skills)** - Curated community skills from the Composio ecosystem
- **[wshobson/agents](https://github.com/wshobson/agents)** - Development skills inspired by their plugin marketplace patterns

We believe in open source and giving credit where it's due. If you see your work here and want additional attribution, [open an issue](https://github.com/skillcreatorai/Ai-Agent-Skills/issues).

## Community

- Follow [@skillcreatorai](https://x.com/skillcreatorai) for updates
- [Open an issue](https://github.com/skillcreatorai/Ai-Agent-Skills/issues) for bugs or requests
- [Read CONTRIBUTING.md](./CONTRIBUTING.md) to add skills

---

<p align="center">
  <sub>Built with care by <a href="https://skillcreator.ai">SkillCreator.ai</a></sub>
</p>
