---
allowed-tools: Bash(git add:*), Bash(git status:*), Bash(git commit:*), Bash(git diff:*), Bash(git branch:*), Bash(git push:*)
description: Analyze changes and create a well-crafted git commit
---

# Smart Git Commit

<analyze_changes>
## Step 1: Analyze Repository State

Current repository state:
- Git status: !`git status --porcelain`
- Staged changes: !`git diff --cached --name-status`
- Unstaged changes: !`git diff --name-status`
- Current branch: !`git branch --show-current`

**Feature context:**
- Check for active features: !`find docs/specs -name "status.md" -exec grep -l "in_progress\|active" {} \; 2>/dev/null || echo "No active features"`

Analyze the changes and determine the appropriate commit type and scope.
</analyze_changes>

<generate_message>
## Step 2: Generate Commit Message

**Commit Type Rules:**
- New component/API → `feat(scope): Add X`
- Bug fixes → `fix: Resolve Y`
- Tests only → `test: Cover Z`
- Documentation → `docs: Update X`
- Refactoring → `refactor: Improve X`
- Multiple changes → Group by primary change

**Format:** `type(scope): brief description`
- Keep subject under 50 characters
- Use imperative mood ("Add" not "Added")
- Include feature context from specs if applicable

Show suggested message: "📝 **Suggested:** `[generated message]`"
</generate_message>

<execute_commit>
## Step 3: Execute Commit

If the suggestion looks good, execute:
- Stage all changes: `git add -A`
- Create commit: `git commit -m "[message]"`
- Confirm: "✅ **Committed!** Ready for `git push`"
</execute_commit>

Focus on creating commits that clearly explain what changed and why.
