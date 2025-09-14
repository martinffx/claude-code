---
allowed-tools: Bash(npm:*), Bash(echo:*)
description: Validate code changes with build, lint, and test pipeline
---

# Validate Changes

<detect_project>
## Step 1: Detect Project Type

**Project detection:**
- Check for package.json (Node.js)
- Check for Cargo.toml (Rust)
- Check for go.mod (Go)
- Check for pyproject.toml/requirements.txt (Python)
- Check for Makefile (Make)

**Run appropriate commands:**

**Node.js Project:**
!`npm run build || echo "❌ Build failed"`
!`npm run lint:fix || echo "❌ Lint errors remain"`
!`npm test || echo "❌ Tests failed"`

**Python Project:**
!`python -m pytest || echo "❌ Tests failed"`
!`ruff check --fix || echo "❌ Lint errors remain"`
!`mypy . || echo "❌ Type check failed"`

**Rust Project:**
!`cargo test || echo "❌ Tests failed"`
!`cargo clippy || echo "❌ Lint errors remain"`
!`cargo build || echo "❌ Build failed"`

**Go Project:**
!`go test ./... || echo "❌ Tests failed"`
!`go vet ./... || echo "❌ Lint errors remain"`
!`go build ./... || echo "❌ Build failed"`
</detect_project>

<analyze_results>
## Step 2: Results Analysis

Based on the validation results above:

**If all passed:**
✅ **Ready to commit!** All quality gates passed.

**If any failed:**
❌ **Fix required** - Review the specific errors above and address:

- **Build failures** → Check TypeScript errors, missing dependencies
- **Lint errors** → Review remaining style/code quality issues
- **Test failures** → Fix failing tests or update test expectations

**Next action:** Fix the issues and run `/validate` again before committing.
</analyze_results>
