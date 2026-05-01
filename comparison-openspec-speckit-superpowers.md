# Deep Comparison: OpenSpec vs GitHub Spec-Kit vs Obra Superpowers

> Investigation Date: 2026-05-01
> Scope: Comparing three spec-driven development and agentic coding frameworks

---

## Executive Summary

| Dimension | OpenSpec | GitHub Spec-Kit | Obra Superpowers |
|-----------|----------|-----------------|------------------|
| **Type** | Spec-driven framework (CLI) | Spec-driven toolkit (CLI + extensions) | Skills framework & methodology |
| **Author** | Fission AI | GitHub | Jesse Vincent (obra) |
| **Language** | JavaScript/TypeScript (Node.js) | Python | Shell scripts + Markdown |
| **Install** | `npm install -g @fission-ai/openspec` | `uv tool install` or `pipx` | Git clone + local install |
| **Philosophy** | "Specs as the source of truth" | "Constitution → Specify → Plan → Implement" | "Skills-based, systematic development" |
| **Stars** | N/A (npm-based) | ~800 (as of May 2026) | ~175k |
| **Forks** | N/A | ~50 | ~15.5k |
| **Community** | Growing (20+ tools supported) | GitHub-backed (50+ extensions) | Large (established) |

---

## 1. OpenSpec (openspec.dev)

### Overview

OpenSpec is a **lightweight, spec-driven development framework** created by Fission AI. It emphasizes keeping specifications as the primary artifact alongside code, enabling AI coding tools to understand requirements through structured specs rather than ad-hoc prompts.

### Key Features

1. **Intent Review via Spec Deltas**
   - Tracks requirement changes across iterations
   - Shows what changed in requirements, not just code
   - Prevents "prompt drift" where AI loses context of original goals

2. **Persistent Context**
   - Specs live in `openspec/specs/` directory alongside code
   - No external dependencies or API keys required
   - Self-contained within the repository

3. **Proposal Generation**
   - Generates design documents and task breakdowns in seconds
   - Creates `proposal.md`, `design.md`, `tasks.md`
   - Tracks all changes in `openspec/changes/`

4. **Universal Compatibility**
   - Supports 20+ AI coding tools without modification
   - No MCP (Model Context Protocol) required
   - Works with Claude Code, Cursor, Codex, Copilot, OpenCode, etc.

5. **Spec Format**
   - Markdown-based with Gherkin-style scenarios
   - Human-readable and version-control friendly
   - Structured enough for AI parsing

### Architecture

```
repo/
├── openspec/
│   ├── specs/
│   │   ├── feature-name.md    # Gherkin-style scenarios
│   │   └── ...
│   └── changes/
│       ├── proposal.md        # Design proposals
│       ├── design.md          # Architecture decisions
│       ├── tasks.md           # Task breakdowns
│       └── specs/             # Versioned specs
└── src/                       # Your code
```

### Workflow

1. Write/modify specs in `openspec/specs/`
2. OpenSpec generates proposals showing intent changes
3. Review deltas before implementation
4. AI coding tools implement based on approved specs
5. Changes tracked in `openspec/changes/`

### Strengths

- ✅ Zero configuration for most use cases
- ✅ No API keys or external services
- ✅ Works with virtually all AI coding tools
- ✅ Human-readable spec format
- ✅ Version-controlled specifications
- ✅ Prevents requirement drift

### Weaknesses

- ❌ Newer project (less mature ecosystem)
- ❌ Workspace/team features not yet available
- ❌ Limited extensibility compared to competitors
- ❌ JavaScript/Node.js dependency

---

## 2. GitHub Spec-Kit (github/spec-kit)

### Overview

Spec-Kit is GitHub's official toolkit for **spec-driven development**. It provides a structured workflow for defining specifications, planning implementations, and coordinating with AI coding agents. It emphasizes "constitution" (project governance) as the foundation.

### Key Features

1. **Constitution-Driven Workflow**
   - `/speckit.constitution` - Define project rules, constraints, patterns
   - `/speckit.specify` - Create detailed specifications
   - `/speckit.plan` - Generate implementation plans
   - `/speckit.tasks` - Break down into tasks
   - `/speckit.implement` - Execute with AI agents

2. **Rich Extension Ecosystem**
   - 50+ community extensions
   - Categories: docs, code, process, integration, visibility
   - Templates and presets for common patterns
   - Workflow extensions for CI/CD integration

3. **Project Governance (AGENTS.md)**
   - Central project configuration file
   - Defines coding standards, constraints, patterns
   - AI agents read AGENTS.md for context
   - Evolves with the project

4. **Multi-Agent Integration**
   - Works with Claude, Cursor, Copilot, and others
   - Agent-aware specification format
   - Task delegation between agents

5. **Python-Based CLI**
   - `specify-cli` command-line tool
   - Installable via `uv tool install` or `pipx`
   - Cross-platform support

### Architecture

```
repo/
├── AGENTS.md                  # Project constitution
├── .speckit/
│   ├── extensions/            # Installed extensions
│   ├── templates/             # Reusable templates
│   ├── workflows/             # Custom workflows
│   └── presets/               # Configuration presets
├── specs/
│   ├── *.spec.md              # Specification files
│   └── index.json             # Spec registry
└── src/                       # Your code
```

### Workflow

1. **Constitute**: Define `AGENTS.md` with project rules
2. **Specify**: Write specs using `/speckit.specify`
3. **Plan**: Generate implementation plan with `/speckit.plan`
4. **Task**: Break into actionable tasks with `/speckit.tasks`
5. **Implement**: Execute with AI agent via `/speckit.implement`

### Extension Categories

| Category | Purpose | Examples |
|----------|---------|----------|
| **Docs** | Documentation generation | API docs, README generators |
| **Code** | Code-specific tools | Linters, formatters, type checkers |
| **Process** | Workflow automation | PR templates, review workflows |
| **Integration** | External tool integration | CI/CD, issue trackers |
| **Visibility** | Project insights | Metrics, dashboards |

### Strengths

- ✅ Official GitHub backing
- ✅ Rich extension ecosystem
- ✅ Strong project governance model
- ✅ Multi-agent support
- ✅ Templates and presets for quick start
- ✅ Python-based (accessible to many developers)

### Weaknesses

- ❌ Smaller community than Superpowers
- ❌ Newer project (evolving rapidly)
- ❌ Requires Python toolchain
- ❌ More complex setup for simple projects

---

## 3. Obra Superpowers (github/obra/superpowers)

### Overview

Superpowers is a **mature skills framework and software development methodology** created by Jesse Vincent (obra). It takes a "skills-based" approach to agentic development, providing composable skills that can be combined for complex workflows. It emphasizes systematic development practices like TDD and code review.

### Key Features

1. **Skills-Based Architecture**
   - Composable, reusable skills
   - Skills are self-contained with clear boundaries
   - Plugin-based design (zero external dependencies)
   - Skills can be combined for complex workflows

2. **Comprehensive Workflow**
   - `brainstorming` → Explore and design
   - `using-git-worktrees` → Isolated development environments
   - `writing-plans` → Create implementation plans
   - `subagent-driven-development` / `executing-plans` → Execute
   - `test-driven-development` → Write tests first
   - `requesting-code-review` → Quality assurance
   - `finishing-a-development-branch` → Clean integration

3. **Skill Categories**

   | Category | Skills | Purpose |
   |----------|--------|---------|
   | **Testing** | `test-driven-development` | TDD methodology |
   | **Debugging** | `systematic-debugging`, `verification-before-completion` | Quality assurance |
   | **Collaboration** | `brainstorming`, `writing-plans`, `executing-plans`, `dispatching-parallel-agents`, `code-review`, `using-git-worktrees`, `finishing-branch`, `subagent-driven-development` | Team coordination |
   | **Meta** | `writing-skills`, `using-superpowers` | Framework extension |

4. **Philosophy**
   - Test-Driven Development (TDD) as default
   - Systematic over ad-hoc approaches
   - Complexity reduction through decomposition
   - Evidence over claims (verification before completion)
   - Quality over speed

5. **Multi-Platform Support**
   - Claude, Codex, Cursor, OpenCode, Copilot, Gemini
   - Platform-agnostic skill definitions
   - Consistent behavior across tools

### Architecture

```
superpowers/
├── skills/
│   ├── brainstorming/
│   ├── test-driven-development/
│   ├── writing-plans/
│   ├── executing-plans/
│   ├── subagent-driven-development/
│   ├── dispatching-parallel-agents/
│   ├── systematic-debugging/
│   ├── verification-before-completion/
│   ├── requesting-code-review/
│   ├── receiving-code-review/
│   ├── finishing-a-development-branch/
│   ├── using-git-worktrees/
│   ├── writing-skills/
│   └── using-superpowers/
├── docs/
└── plugins/                   # Zero-dependency plugin system
```

### Workflow

1. **Brainstorm**: Use `brainstorming` skill to explore requirements
2. **Isolate**: Create git worktree for isolated development
3. **Plan**: Write detailed implementation plan
4. **Develop**: Execute plan with subagent-driven development
5. **Test**: Follow TDD - write tests before code
6. **Review**: Request code review for quality
7. **Finish**: Clean branch integration

### Strengths

- ✅ Mature and well-established (175k+ stars)
- ✅ Comprehensive methodology covering full SDLC
- ✅ Skills are composable and reusable
- ✅ Zero-dependency plugin design
- ✅ Strong emphasis on quality (TDD, code review)
- ✅ Large community and ecosystem
- ✅ Multi-platform support

### Weaknesses

- ❌ More opinionated than alternatives
- ❌ Steeper learning curve
- ❌ Requires commitment to methodology
- ❌ Shell script-based (less accessible to some)

---

## 4. Detailed Comparison

### 4.1 Philosophy & Approach

| Aspect | OpenSpec | Spec-Kit | Superpowers |
|--------|----------|----------|-------------|
| **Core Idea** | Specs as source of truth | Constitution-driven specs | Skills-based methodology |
| **Governance** | Minimal (self-contained) | AGENTS.md constitution | Skill conventions |
| **Quality Focus** | Spec review (deltas) | Spec completeness | TDD + code review |
| **Flexibility** | High (minimal structure) | Medium (workflow-driven) | Lower (opinionated) |
| **Learning Curve** | Low | Medium | Higher |

### 4.2 Technical Architecture

| Aspect | OpenSpec | Spec-Kit | Superpowers |
|--------|----------|----------|-------------|
| **Language** | JavaScript/TypeScript | Python | Shell + Markdown |
| **Dependencies** | Node.js | Python (uv/pipx) | None (zero-dep) |
| **Storage** | Files in repo | Files + config | Files in repo |
| **Extensibility** | Limited | Rich (50+ extensions) | Plugin-based |
| **Format** | Markdown + Gherkin | Markdown specs | Markdown skills |
| **Version Control** | Native Git | Native Git | Native Git |

### 4.3 AI Agent Integration

| Feature | OpenSpec | Spec-Kit | Superpowers |
|---------|----------|----------|-------------|
| **Supported Tools** | 20+ (universal) | Multiple (Claude, Cursor, etc.) | 6+ major platforms |
| **Integration Method** | File-based specs | CLI + extensions | Skills invocation |
| **Context Passing** | Spec files | AGENTS.md + specs | Skill context |
| **Multi-Agent** | Implicit | Supported | Supported |
| **Agent Awareness** | Tool-agnostic | Agent-aware | Agent-agnostic |

### 4.4 Workflow Comparison

```
OpenSpec:           Spec-Kit:                    Superpowers:
┌─────────────┐     ┌─────────────┐              ┌─────────────┐
│ Write Spec  │     │ Constitution│              │ Brainstorm  │
└──────┬──────┘     └──────┬──────┘              └──────┬──────┘
       ↓                   ↓                            ↓
┌─────────────┐     ┌─────────────┐              ┌─────────────┐
│Review Delta │     │  Specify    │              │ Git Worktree│
└──────┬──────┘     └──────┬──────┘              └──────┬──────┘
       ↓                   ↓                            ↓
┌─────────────┐     ┌─────────────┐              ┌─────────────┐
│ Implement   │     │    Plan     │              │ Write Plan  │
└──────┬──────┘     └──────┬──────┘              └──────┬──────┘
       ↓                   ↓                            ↓
┌─────────────┐     ┌─────────────┐              ┌─────────────┐
│ Track Change│     │   Tasks     │              │  Execute    │
└─────────────┘     └──────┬──────┘              └──────┬──────┘
                          ↓                            ↓
                   ┌─────────────┐              ┌─────────────┐
                   │  Implement  │              │ TDD + Review│
                   └─────────────┘              └──────┬──────┘
                                                       ↓
                                                ┌─────────────┐
                                                │   Finish    │
                                                └─────────────┘
```

### 4.5 Spec/Skill Format Comparison

#### OpenSpec Spec Format
```markdown
# Feature: User Authentication

## Scenario: Successful login
- Given a user with email "user@example.com"
- When they enter correct password
- Then they should be authenticated
- And redirected to dashboard

## Scenario: Failed login
- Given a user with email "user@example.com"
- When they enter wrong password
- Then they should see error message
- And remain on login page
```

#### Spec-Kit Spec Format
```markdown
# Specification: User Authentication

## Constitution
- All auth must use OAuth 2.0
- Passwords must be hashed with bcrypt

## Requirements
1. Users can login with email/password
2. Failed attempts are rate-limited
3. Sessions expire after 24 hours

## Implementation Notes
- Use existing auth library
- Add middleware for session validation
```

#### Superpowers Skill Format
```markdown
# Skill: Test-Driven Development

## Purpose
Guide development through test-first methodology

## Invocation
When implementing any feature or bugfix

## Steps
1. Write failing test
2. Implement minimal code to pass
3. Refactor while keeping tests green
4. Verify with evidence before completion

## Constraints
- Never suppress type errors
- Evidence required before claiming done
```

### 4.6 Community & Ecosystem

| Aspect | OpenSpec | Spec-Kit | Superpowers |
|--------|----------|----------|-------------|
| **Community Size** | Growing | Small but active | Large (175k stars) |
| **Extensions** | Limited | 50+ official/community | Skills ecosystem |
| **Documentation** | Good | Good | Excellent |
| **Maturity** | Newer (2025+) | Newer (2025+) | Established |
| **Backing** | Fission AI | GitHub | Individual (obra) |
| **License** | Open source | Open source | Open source |

---

## 5. Use Case Recommendations

### Choose OpenSpec When:

- ✅ You want minimal setup and configuration
- ✅ You need universal compatibility with AI tools
- ✅ Your team prefers lightweight, file-based specs
- ✅ You want to prevent prompt drift with spec deltas
- ✅ You prefer Gherkin-style scenario definitions
- ✅ You don't need complex governance or workflows

**Best for**: Small to medium teams, rapid prototyping, teams using diverse AI tools

### Choose Spec-Kit When:

- ✅ You want structured governance with AGENTS.md
- ✅ You need rich extensions and templates
- ✅ You prefer Python-based tooling
- ✅ You want GitHub-backed project support
- ✅ You need workflow automation (CI/CD integration)
- ✅ You want constitution-driven development

**Best for**: Teams wanting governance, GitHub-centric workflows, structured specifications

### Choose Superpowers When:

- ✅ You want comprehensive methodology covering full SDLC
- ✅ You value TDD and systematic debugging
- ✅ You need composable, reusable skills
- ✅ You want zero-dependency plugin system
- ✅ You prefer established, battle-tested approach
- ✅ You need skills for collaboration and code review

**Best for**: Teams committed to quality, larger projects, systematic development practices

---

## 6. Hybrid Approaches

These tools are not mutually exclusive. Consider combining them:

### OpenSpec + Superpowers
- Use OpenSpec for spec definition and delta tracking
- Use Superpowers skills for TDD and code review
- Best of both: lightweight specs + comprehensive methodology

### Spec-Kit + Superpowers
- Use Spec-Kit for governance and specification
- Use Superpowers skills for implementation and testing
- Combines constitution-driven specs with systematic development

### All Three
- Spec-Kit AGENTS.md for governance
- OpenSpec for detailed feature specifications
- Superpowers for implementation workflow
- Most comprehensive but highest overhead

---

## 7. Conclusion

### Summary Table

| Criteria | Winner | Notes |
|----------|--------|-------|
| **Ease of Use** | OpenSpec | Minimal setup, intuitive |
| **Governance** | Spec-Kit | AGENTS.md constitution |
| **Comprehensiveness** | Superpowers | Full SDLC coverage |
| **Flexibility** | OpenSpec | Tool-agnostic, minimal |
| **Extensibility** | Spec-Kit | 50+ extensions |
| **Quality Assurance** | Superpowers | TDD + review built-in |
| **Community** | Superpowers | 175k stars |
| **Maturity** | Superpowers | Established, stable |
| **Innovation** | OpenSpec | Spec deltas, universal |
| **Integration** | Spec-Kit | CI/CD, templates |

### Final Recommendation

- **Start with OpenSpec** if you're new to spec-driven development or need something lightweight
- **Adopt Spec-Kit** if you need governance and want GitHub's backing
- **Commit to Superpowers** if you're building large projects and value systematic quality

For most teams, starting with **OpenSpec** for spec management and gradually incorporating **Superpowers** skills for quality assurance provides the best balance of simplicity and rigor.

---

*Document generated by SteamedFish's Agent - 2026-05-01*
*Sources: openspec.dev, github.com/spec-kit, github.com/obra/superpowers*
