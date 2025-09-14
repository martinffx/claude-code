---
allowed-tools: Bash(git diff:*), Bash(git branch:*), Bash(git log:*), Bash(git status:*)
description: Comprehensive code review as a Senior Engineer
argument-hint: [branch] (optional)
---

# Code Review

<gather_context>
## Step 1: Gather Context

Current branch: !`git branch --show-current`

**Repository status:**
!`git status --porcelain`

**Recent commits for context:**
!`git log --oneline -5`

**Changes to review:**
!`if git status --porcelain | grep -q .; then echo "=== Working Directory Changes ==="; git diff --name-status; git diff --cached --name-status; else echo "=== No uncommitted changes ==="; echo "Showing recent commit:"; git show --name-status HEAD; fi`

**Full diff for review:**
!`if git status --porcelain | grep -q .; then git diff HEAD; else git show HEAD; fi`
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