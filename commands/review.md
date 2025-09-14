---
allowed-tools: Bash(git diff:*), Bash(git branch:*), Bash(git log:*), Bash(git status:*), Bash(git show:*), Bash(echo:*)
description: Comprehensive code review as a Senior Engineer
argument-hint: [branch] (optional)
---

# Code Review

<gather_context>
## Step 1: Gather Context

Current branch: !`git branch --show-current`

**Repository status:**
!`git status --porcelain`

**Recent commits (if any):**
!`git log --oneline -5 2>/dev/null || echo "No commits yet"`

**Staged changes:**
!`git diff --cached --name-status`

**Unstaged changes:**
!`git diff --name-status`

**Full diff for review:**
!`git diff HEAD 2>/dev/null || git diff --cached`
</gather_context>

<review_analysis>
## Step 2: Senior Engineer Review

<subagent name="analyst">
Analyze all changes with focus on:

**🔴 CRITICAL:** Security vulnerabilities, data loss risks, breaking changes
**🟡 IMPORTANT:** Bugs, performance issues, maintainability concerns
**🟢 MINOR:** Style inconsistencies, naming improvements, optimizations

**Architecture Compliance:**
- Check against docs/standards/tech.md patterns
- Verify layered architecture: Router → Service → Repository → Entity
- Ensure proper Entity transformations (fromRequest, toRecord, toResponse)
- Validate stub-driven TDD patterns per docs/standards/coding.md

Generate specific, actionable feedback that helps improve code quality and maintainability.
</subagent>
</review_analysis>

<output_format>
## Step 3: Review Report

**Summary:** Brief overview of changes and overall assessment

**Issues by Severity:**
- `🔴 file:line - Issue description → Suggested fix`
- `🟡 file:line - Issue description → Suggested fix`
- `🟢 file:line - Issue description → Suggested fix`

**👍 Good:** Highlight positive aspects of the code
</output_format>