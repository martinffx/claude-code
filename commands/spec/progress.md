---
description: Update task progress and executive summary in tasks.md
argument-hint: [feature_name]
---

# Update Feature Progress

<update_tasks>
## Step 1: Update Task Checklists

<subagent name="context">
Load the tasks.md file from docs/specs/$FEATURE_NAME/ for the specified feature.

Update task checkboxes based on actual implementation progress:
- Check completed tasks: `[ ]` → `[x]`
- Verify implementation exists in codebase
- Leave incomplete tasks unchecked
</subagent>
</update_tasks>

<update_summary>
## Step 2: Refresh Executive Summary

<subagent name="product">
Calculate and update executive summary metrics in tasks.md:

- **Total Phases**: Count of domain sections
- **Critical Path**: Identify dependency-blocking phases
- **Parallel Execution**: Count independent domains
- **Estimated Effort**: Total tasks vs completed tasks

Update the executive summary section with current metrics.
</subagent>
</update_summary>

## ✅ Tasks Updated

Feature tasks.md has been updated with:
- Current task completion status
- Refreshed executive summary metrics
- Accurate progress tracking

**Continue with**: `/spec:implement` for next tasks
