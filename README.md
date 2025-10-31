# BDD Workflow Orchestrator Plugin

A comprehensive BDD workflow orchestration framework for Claude Code that coordinates specialized agents to implement features, validate quality, and capture patterns across all your projects.

---

## Prerequisites

Before installing this plugin, you need:

1. **Claude Code installed** - [Install Claude Code](https://docs.claude.com/en/docs/claude-code/quickstart)
2. **A Claude.ai account** or Claude Console API account

---

## Quick Install

### For Individual Users

```bash
# Install from GitHub
/plugin marketplace add https://github.com/tamas-hamszabo/bdd-orchestrator-plugin
/plugin install bdd-orchestrator
```

### For Teams (Recommended)

Add to your repository's `.claude/settings.json`:

```json
{
  "plugins": {
    "marketplaces": [
      "https://github.com/tamas-hamszabo/bdd-orchestrator-plugin"
    ],
    "enabledPlugins": [
      "bdd-orchestrator"
    ]
  }
}
```

When team members trust your repository folder, Claude Code automatically installs the plugin.

---

## What's Included

### 12 Specialized Agents

| Agent | Purpose |
|-------|---------|
| **architect** | Creates surgical-precision implementation plans maximizing code reuse |
| **code-reviewer** | Reviews code for security, performance, and maintainability |
| **implementation** | Implements features following architectural plans |
| **tester** | Creates and runs comprehensive test suites |
| **feature-generator** | Generates detailed user stories from requirements |
| **code-researcher** | Discovers reusable components in codebase |
| **agent-qa** | Validates agent outputs against quality standards |
| **memorizing-feedback** | Extracts and applies patterns from user feedback |
| **research** | Researches best practices and solutions |
| **root-cause-analysis** | Diagnoses bugs and system issues |
| **ac-review** | Reviews acceptance criteria and implementation plans |
| **claude-setup** | Expert in Claude Code configuration |

### 11 Agent Skills

- **code-research** - Codebase analysis for reuse opportunities
- **architectural-thinking** - Strategic architecture decisions
- **surgical** - Ultra-minimal scope with 100% delivery
- **critical-thinking** - Deep reasoning and validation
- **data-flow-tracing** - System data flow understanding
- **agent-reporting** - Standardized agent output formatting
- **qa-feedback-loop** - Quality validation loops
- **parallel** - Parallel task execution
- **checkpoint-resume** - Save and resume workflows
- **best-practices** - Domain-specific best practices
- **story-folder-setup** - Intelligent story folder management

### 7 Automated Workflows

1. **New Feature** - Complete feature development with tests and review
2. **Bug Fix** - Efficient bug fixes with research reuse
3. **Create Plan** - Explore feasibility without implementation
4. **Find Bug** - Diagnose root cause without fixing
5. **Single Agent** - Execute individual agent with QA
6. **Story Tester** - Comprehensive story validation
7. **Question** - Answer code questions via analysis

### BDD Orchestrator

Intelligent request routing that:
- Classifies every user request
- Executes appropriate workflow
- Invokes specialized agents
- Validates outputs at quality gates
- Reports completion with metrics

---

## How It Works

1. **You make a request**: "Build a dark mode toggle feature"
2. **Orchestrator classifies**: Routes to NEW FEATURE workflow
3. **Workflow executes**:
   - feature-generator creates detailed story
   - code-researcher finds reusable components
   - architect creates implementation plan
   - ac-review validates the plan
   - implementation builds the feature
   - tester creates and runs tests
   - code-reviewer validates quality
   - agent-qa checks all outputs
4. **You get results**: Complete, tested, reviewed feature

---

## Usage Examples

### Build a New Feature

```
You: Build a CSV export feature for the users table

Orchestrator:
→ Routes to NEW FEATURE workflow
→ Invokes feature-generator
→ Invokes code-researcher
→ Invokes architect
→ Invokes ac-review
→ Invokes implementation
→ Invokes tester
→ Invokes code-reviewer
→ Invokes agent-qa

Result: Complete feature with tests and review
```

### Fix a Bug

```
You: The login timeout is too short

Orchestrator:
→ Routes to BUG FIX workflow
→ Documents the issue
→ Checks for existing research
→ Performs targeted research
→ Runs root-cause-analysis
→ Creates fix plan
→ Implements fix
→ Runs tests
→ Reviews changes

Result: Bug fixed with minimal scope
```

### Plan Without Implementing

```
You: Plan an approach for multi-tenant data isolation

Orchestrator:
→ Routes to CREATE PLAN workflow
→ Generates detailed story
→ Researches existing patterns
→ Creates architectural plan
→ Reviews plan

Result: Comprehensive plan ready for review (no code changes)
```

---

## Architecture

```
┌─────────────────────────────────────────┐
│         BDD Orchestrator                │
│         (CLAUDE.md)                     │
│  - Request classification               │
│  - Workflow routing                     │
│  - Agent coordination                   │
└─────────────────────────────────────────┘
                  │
      ┌───────────┴───────────┐
      ▼                       ▼
┌─────────────┐         ┌─────────────┐
│  Workflows  │         │   Agents    │
│             │         │             │
│ • New       │────────▶│ • architect │
│   Feature   │         │ • reviewer  │
│ • Bug Fix   │         │ • tester    │
│ • Create    │         │ • etc.      │
│   Plan      │         │             │
│ • etc.      │         └─────────────┘
└─────────────┘                │
                               ▼
                         ┌─────────────┐
                         │   Skills    │
                         │             │
                         │ • code-     │
                         │   research  │
                         │ • surgical  │
                         │ • etc.      │
                         └─────────────┘
```

---

## Directory Structure

```
bdd-orchestrator-plugin/
├── .claude-plugin/
│   ├── plugin.json              # Plugin manifest
│   └── marketplace.json         # Marketplace config
├── agents/                       # 12 specialized agents
│   ├── architect/
│   ├── code-reviewer/
│   ├── implementation/
│   └── ... (9 more)
├── skills/                       # 11 agent skills
│   ├── code-research/
│   ├── architectural-thinking/
│   └── ... (9 more)
├── workflows/                    # 7 automated workflows
│   ├── new-feature-workflow.md
│   ├── bug-fix-workflow.md
│   └── ... (5 more)
├── hooks/                        # Event handlers
├── templates/                    # Story and pattern templates
├── examples/                     # Example configurations
│   ├── memory-template/         # Technology stack template
│   └── stories-template/        # Story folder template
├── docs/                         # Documentation
│   └── QUICK_START.md           # Quick start guide
├── CLAUDE.md                     # BDD orchestrator
├── settings.json                 # Plugin settings
├── README.md                     # This file
├── CHANGELOG.md                  # Version history
└── LICENSE                       # MIT license
```

---

## Configuration

### Project-Specific Settings

Each project using this plugin should have:

#### `.memory/TECHNOLOGY_STACK.md`

Defines your project's technology stack:

```markdown
# Technology Stack

## Languages
- TypeScript 5.x
- Node.js 20.x

## Framework
- Next.js 14.x
- React 18.x

## Testing
- Jest for unit tests
- Playwright for E2E tests

[... etc ...]
```

#### `.claude/stories/[story-name]/`

Each feature gets a story folder:

```
.claude/stories/dark-mode-toggle/
├── STORY.md                    # User story and ACs
├── RESEARCH.md                 # Reusable components found
├── PLAN.md                     # Implementation plan
├── TEST_RESULTS.md             # Test execution results
└── REVIEW.md                   # Code review results
```

---

## Getting Started

### 1. Install the Plugin

```bash
/plugin marketplace add https://github.com/tamas-hamszabo/bdd-orchestrator-plugin
/plugin install bdd-orchestrator
```

### 2. Verify Installation

```bash
# List installed agents
/agents

# You should see 12 agents from this plugin
```

### 3. Create Your Technology Stack

```bash
# In your project root
mkdir -p .memory
```

Create `.memory/TECHNOLOGY_STACK.md` with your project's tech stack.

### 4. Make Your First Request

```
Build a dark mode toggle feature
```

The orchestrator will route to NEW FEATURE workflow and guide you through the process.

---

## Documentation

- **[Quick Start Guide](docs/QUICK_START.md)** - Get started quickly
- **Agent Reference** - Detailed agent documentation
- **Workflow Guide** - How each workflow works
- **Skills Reference** - Available skills and usage
- **Team Setup** - Setting up for teams
- **Troubleshooting** - Common issues and solutions

---

## Updates

### Check for Updates

```bash
/plugin update bdd-orchestrator
```

### Force Reinstall

```bash
/plugin uninstall bdd-orchestrator
/plugin install bdd-orchestrator
```

---

## Contributing

Contributions welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

---

## License

MIT License - See [LICENSE](LICENSE) file for details

---

## Support

- **Issues**: [GitHub Issues](https://github.com/tamas-hamszabo/bdd-orchestrator-plugin/issues)
- **Documentation**: [docs/](docs/)

---

## Acknowledgments

Built with [Claude Code](https://claude.com/claude-code) and inspired by BDD best practices.

---

## Supported By

**Made with ❤️ for development teams** 
This project is proudly supported by **[SAAS First](https://saasfirst.com)**.
