---
description: Generate implementation tasks from technical design
argument-hint: <feature_name>
---

# Phase Planning: $FEATURE_NAME

<analyze_implementation>
## Step 1: Generate Domain-Phase Implementation Plan

<subagent name="architect">
Use the sequential thinking tool to create domain-based phases:

Read:
- `docs/specs/$FEATURE_NAME/design.json`
- `docs/specs/$FEATURE_NAME/design.md`

For each domain identified in design:
- Create phase with Entity → Repository → Service → Router tasks
- Each task follows stub-driven TDD (reference docs/standards/coding.md)
- Define inter-phase dependencies
- Generate tasks with 3 sub-steps: stub → test → implement

### Output: `docs/specs/$FEATURE_NAME/plan.json`
```json
{
  "phases": {
    "user_domain": {
      "name": "User Domain",
      "dependencies": [],
      "tasks": ["user_entity", "user_repository", "user_service", "user_router"]
    },
    "order_domain": {
      "name": "Order Domain",
      "dependencies": ["user_domain"],
      "tasks": ["order_entity", "order_repository", "order_service", "order_router"]
    }
  },
  "tasks": {
    "user_entity": {
      "phase": "user_domain",
      "order": 1,
      "tdd_steps": ["test", "implement", "refactor"]
    }
  }
}
```
</subagent>
</analyze_implementation>


<prioritize_implementation>
## Step 2: Optimize Phase and Task Dependencies

<subagent name="product">
Use the sequential thinking tool to optimize implementation order:

Read:
- `docs/specs/$FEATURE_NAME/plan.json`

Analyze and optimize:
- Phase dependencies (which domains depend on others)
- Parallel execution opportunities
- Task ordering within phases (Entity first, Router last)
- Multi-agent workflow optimization

### Output: `docs/specs/$FEATURE_NAME/plan.json`

Update with optimized phase execution and task ordering within phases
</subagent>
</prioritize_implementation>

<write_documentation>
## Step 3: Create Task Documentation

<subagent name="scaffold">

Read:
- `docs/specs/$FEATURE_NAME/plan.json`

Template:
- `~/.claude/docs/templates/specs/tasks.md`

Files created in `docs/specs/$FEATURE_NAME/`:
- `tasks.md` - Human readable checklist following TDD patterns

</subagent>
</write_documentation>

## ✅ Phase Planning Complete

Generated domain-based implementation plan:
- Phases organized by domain (each domain = one phase)
- Tasks within each phase follow Entity → Repository → Service → Router
- Phase dependencies identified for parallel execution
- Ready to begin implementation

**Next step**: `/spec:implement $FEATURE_NAME`
