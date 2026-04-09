# Claude Dev Boilerplate

A comprehensive, reusable engineering standards kit for [Claude Code](https://claude.ai/claude-code). Drop it into any new project to instantly get production-grade development workflows — TDD, security-first development, multi-agent coordination, automated code formatting, secret detection, and 129+ skills out of the box.

## Why This Exists

Every new project starts the same way: setting up standards, configuring tools, writing the same rules about testing, security, and code quality. This boilerplate captures all of that into a portable package you copy once and never rewrite.

It enforces:
- **Test-Driven Development (TDD)** — tests written before implementation, user journey patterns
- **Security-Driven Development (SDD)** — threat modeling, OWASP Top 10, DAST scanning
- **Contract-First API Design** — TypeScript contracts define the interface before any code is written
- **No God Files** — 300-line hard limit per file, directory-based module structure
- **Dynamic Testing Only** — no static import checks; real HTTP requests, real browser interactions
- **Consistent Naming** — `snake_case` fields, `UPPER_SNAKE_CASE` enums, `PascalCase` components

## Quick Start

### 1. Copy into your project

```bash
# From the boilerplate directory
cp -r /path/to/claude-dev-boilerplate/{.claude,CLAUDE.md,handoff,docs} /path/to/your-project/

# Or clone and copy
git clone https://github.com/goodnessibeh/claude-dev-boilerplate.git
cp -r claude-dev-boilerplate/{.claude,CLAUDE.md,handoff,docs} /path/to/your-project/
```

### 2. Customize for your project

Open `CLAUDE.md` and follow the **Boilerplate Adaptation Instructions** section at the top. Replace placeholders:

- `[Project Name]` → your project name
- `[Your Name]` / `[your@email.com]` → your git identity
- Update UI kit paths or remove if not applicable
- Add project-specific enum values to `docs/contracts/_enums.contract.ts`

### 3. Start building

Claude Code will automatically read `CLAUDE.md` and follow all engineering standards. Every session starts with the same quality bar.

## What's Included

### Engineering Standards (`CLAUDE.md`)

The central document governing all code. Covers:

| Area | What It Enforces |
|------|-----------------|
| **TDD** | Write tests first. Red → Green → Refactor. Every endpoint/component tested. |
| **SDD** | Threat model before implementation. OWASP Top 10. DAST scans. |
| **Architecture** | 300-line file limit. Directory-based modules. No monolithic files. |
| **Database** | N+1 prevention. Cursor pagination. Index optimization. Migration safety. |
| **Security** | Auth + authz on every endpoint. Rate limiting. Audit logging. No hardcoded secrets. |
| **Frontend** | CSS Modules (no inline styles). Mobile-first. Light + dark mode. WCAG 2.1 AA. |
| **Mobile** | StyleSheet companion files. Component-based screens. Detox/Maestro e2e tests. |
| **Naming** | `snake_case` fields, `UPPER_SNAKE_CASE` enums, `PascalCase` components everywhere. |
| **Git** | No AI references in commits. Always `git add .` from root. `IF NOT EXISTS` in migrations. |

### Skills (129 files across 6 categories)

```
.claude/skills/
├── 01-Software-Web-Development/    # Frontend, MCP, Cloudflare, Stripe, webapp testing
├── 02-Context-Engineering-AI/      # Context optimization, prompt engineering, multi-agent
├── 03-Security/                    # Security code review, vibesec
├── 04-QA-Testing/                  # QA testing strategies
├── 05-Document-Processing/         # PDF, DOCX processing
├── 06-Meta-Process/                # Skill creation
├── senior-security/                # Threat modeling, pen testing, crypto implementation
├── senior-qa/                      # Test automation, coverage analysis, e2e scaffolding
├── product-manager-toolkit/        # PRD templates, RICE prioritization, interview analysis
├── frontend-design/                # Production-grade UI design
├── web-perf/                       # Core Web Vitals, performance analysis
├── webapp-testing/                 # Playwright-based web app testing
├── stripe-integration/             # Payment processing patterns
├── mcp-builder/                    # MCP server development
├── test-driven-development/        # TDD workflow
├── verification-before-completion/ # Verify before claiming done
└── ...                             # 20+ more individual skills
```

### Commands (4 slash commands)

| Command | Description |
|---------|------------|
| `/ultra-think` | Multi-framework structured analysis with adversarial reasoning |
| `/create-prd` | Generate Product Requirements Documents |
| `/init-project` | Initialize new project with proper structure |
| `/setup-development-environment` | Configure dev environment with tools and workflows |

### Agents

| Agent | Description |
|-------|------------|
| `database-optimizer` | Query optimization, indexing strategies, performance tuning across PostgreSQL, MySQL, MongoDB |

### Hooks (Auto-configured in `settings.local.json`)

| Hook | Trigger | What It Does |
|------|---------|-------------|
| **Auto-format** | After every file edit | Runs Prettier (JS/TS/CSS/JSON), Black (Python), gofmt (Go), rustfmt (Rust) |
| **Dependency audit** | After editing package.json/requirements.txt/Cargo.toml | Runs `npm audit`, `safety check`, or `cargo audit` |
| **Secret detection** | After every file edit/write | Runs semgrep, bandit (Python), gitleaks, and regex pattern matching |

### Agent Coordination Protocol (`docs/AGENT_COORDINATION.md`)

A complete multi-agent coordination system for large projects:

- **Team structure** — Lead, Backend, Frontend, Mobile, DB, Security, QA agents
- **Contract system** — TypeScript contracts define APIs before implementation
- **Enum convention** — single source of truth in `_enums.contract.ts`
- **Migration protocol** — naming, ordering, conflict resolution
- **Swarm protocol** — how agents hand off work to each other
- **Integration validation** — checklists for backend ↔ frontend ↔ mobile sync
- **File ownership** — which agent owns which files

### Session Handoff System (`handoff/`)

| Template | Purpose |
|----------|---------|
| `HANDOFF_TEMPLATE.md` | End-of-session handoff for continuity between AI sessions |
| `SESSION_MEMORY.md` | Persistent memory across all sessions — architecture decisions, module status, preferences |
| `E2E_TESTING_GUIDE.md` | End-to-end testing patterns and strategies |

### Plugin Marketplace

337 plugin files from the official Claude Code plugin marketplace, including integrations for GitHub, Slack, Discord, Linear, Supabase, Firebase, Playwright, and more.

## Project Structure

```
claude-dev-boilerplate/
├── CLAUDE.md                          # Central engineering standards
├── README.md                          # This file
├── .claude/
│   ├── .mcp.json                      # MCP server configuration
│   ├── settings.local.json            # Permissions, hooks, env vars
│   ├── scripts/
│   │   └── context-monitor.py         # Context window status line
│   ├── agents/
│   │   └── database-optimizer.md      # DB optimization agent
│   ├── commands/
│   │   ├── ultra-think.md
│   │   ├── create-prd.md
│   │   ├── init-project.md
│   │   └── setup-development-environment.md
│   ├── skills/                        # 129 skill files (see above)
│   └── plugins/                       # 337 plugin marketplace files
├── docs/
│   ├── AGENT_COORDINATION.md          # Multi-agent coordination protocol
│   └── contracts/
│       └── _enums.contract.ts         # Master enum definitions (template)
└── handoff/
    ├── HANDOFF_TEMPLATE.md            # Session handoff template
    ├── SESSION_MEMORY.md              # Persistent session memory template
    └── E2E_TESTING_GUIDE.md           # E2E testing guide
```

## Tech Stack Assumptions

This boilerplate is opinionated toward the following stack, but the patterns are adaptable:

| Layer | Default | Adaptable To |
|-------|---------|-------------|
| Backend | Django + DRF | FastAPI, Express, Rails, etc. |
| Database | PostgreSQL | MySQL, MongoDB, etc. |
| Frontend | Next.js + TypeScript + shadcn/ui + Tailwind | React, Vue, Svelte, etc. |
| Mobile | React Native (Expo) | Flutter, SwiftUI, Kotlin |
| State | Zustand | Redux, Jotai, MobX |
| Testing | pytest + Playwright + Detox | Jest, Cypress, Maestro |
| Payments | Stripe/Paystack | Any payment provider |

To adapt for a different stack:
1. Update the backend architecture section in `CLAUDE.md`
2. Modify the frontend rules (CSS modules, shadcn specifics, etc.)
3. Adjust the contract system for your API framework
4. Keep the principles (TDD, SDD, 300-line limit, naming conventions)

## Self-Updating

The `CLAUDE.md` file includes **Boilerplate Adaptation Instructions** that tell any AI model working on the project to continuously update the document as the project evolves. This means:

- Placeholder values get replaced with real project data
- New sections are added as features are built
- Irrelevant sections are removed
- The document stays current — never stale

## License

This boilerplate is free to use for any project. The skills, commands, and plugins retain their original licenses where applicable.

---

Built with [Claude Code](https://claude.ai/claude-code)
