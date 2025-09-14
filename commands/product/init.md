---
description: Initialize project by gathering requirements and creating product documentation
argument-hint: <project_name>
---

# Initialize Project: $PROJECT_NAME

<gather_requirements>
## Step 1: Gather Project Information

<subagent name="analyst">
Conduct structured requirements interview for $PROJECT_NAME.

Gather:
1. Product definition (what are you building - one sentence)
2. Target users (who will use it - be specific)  
3. Core features (3-5 main features)
4. Tech stack preferences (frontend, backend, database)

Structure requirements for documentation.
</subagent>
</gather_requirements>

<create_structure>
## Step 2: Create Project Structure

<subagent name="scaffold">
Create project directory structure and documentation files.

Create:
- `docs/product/` directory with product.md and roadmap.md
- `docs/specs/` directory for feature specifications  
- `docs/standards/` directory with tech.md, style.md, practices.md
- Root CLAUDE.md file with project overview

Apply templates with project data.
</subagent>
</create_structure>

## Step 3: Files Created

The following files are created using the gathered requirements:

### 📄 docs/product/product.md
- Product definition and target users
- Core features list  
- Success metrics

### 📄 docs/product/roadmap.md
- Next 3 features in priority order
- Implementation strategy
- Current status

### 📄 docs/standards/tech.md
- Technology stack choices
- Layered architecture pattern
- Entity transformation patterns

### 📄 docs/standards/style.md
- Code organization and naming conventions
- File structure patterns
- Testing strategies

### 📄 docs/standards/practices.md
- TDD workflow
- Development command sequence
- Quality standards

### 📄 CLAUDE.md
- Project overview and available commands
- Quick start guide

## ✅ Project Initialized

Created documentation structure with:
- Product definition and roadmap
- Technical standards (DDD, TDD, Layered Architecture)
- Development practices
- AI-friendly command reference

**Next action**: `/spec:create authentication` to build your first feature
