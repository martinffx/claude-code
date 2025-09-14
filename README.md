# Claude Code Commands

A structured command system for AI-assisted Spec-Driven Development, enabling rapid feature delivery through systematic specifications and implementation workflows.

## Commands Overview

### 🎯 Product Commands (`/commands/product/`)
- **`/product:init`** - Initialize project with product documentation
- **`/product:roadmap`** - Define and prioritize features
- **`/product:progress`** - Track overall product development

### 📋 Spec Commands (`/commands/spec/`)
- **`/spec:create`** - Create feature specification through structured interview
- **`/spec:design`** - Generate technical design from requirements
- **`/spec:plan`** - Break design into dependency-ordered tasks
- **`/spec:implement`** - Execute implementation using stub-driven TDD
- **`/spec:progress`** - Update task progress and executive summary

### 🛠️ Utility Commands (`/commands/`)
- **`/validate`** - Run build, lint, and test pipeline (multi-language)
- **`/commit`** - Create smart git commits with feature context
- **`/review`** - Comprehensive code review with architecture compliance

## Quick Start

```bash
# 1. Initialize project
/product:init my-project

# 2. Define features
/product:roadmap

# 3. Create & implement feature
/spec:create authentication
/spec:design authentication
/spec:plan authentication
/spec:implement authentication

# 4. Quality assurance
/validate
/review
/commit
```

## Architecture

### Spec-Driven Development
- **Lightweight docs** over heavy planning
- **Dependency-driven** task ordering
- **AI-assisted** implementation
- **Prevention over debugging**

### Technical Standards
- **Layered Architecture**: Router → Service → Repository → Entity
- **Stub-Driven TDD**: Stubs → Tests → Implementation
- **Sequential Thinking**: Structured AI reasoning
- **Agent Specialization**: Focused roles for complex tasks

### File Organization
```
docs/
├── product/           # Product vision & roadmap
├── specs/{feature}/   # Feature specifications & progress
└── standards/         # Technical patterns & practices

commands/
├── product/          # Product management commands
├── spec/            # Feature development commands
└── README.md        # Command documentation
```

## Key Features

- **State Management**: JSON intermediates preserve context between AI agents
- **Multi-Language**: Auto-detects Node.js, Python, Rust, Go, Make projects
- **Progress Tracking**: Real-time task completion updates
- **Architecture Compliance**: Automated pattern validation
- **Smart Commits**: Context-aware git messages

## Best Practices

1. **Follow workflow sequence**: product → spec → implementation
2. **Complete phases**: Don't skip steps in the process
3. **Validate frequently**: Use `/validate` before commits
4. **Track progress**: Update after each implementation task

This system transforms AI from requiring constant prompting into a team member that understands your standards, business context, and implementation approach.
