---
description: Track overall product development progress
argument-hint: [verbose]
---

# Product Development Progress

<load_project_state>
## Step 1: Load Project State

<subagent name="context">
Gather comprehensive project data.

Retrieve:
- Current roadmap from `docs/product/roadmap.md`
- All feature specifications from `docs/specs/*/`
- Feature completion status from `docs/specs/*/status.md`

Load all project state data.
</subagent>
</load_project_state>

<analyze_progress>
## Step 2: Analyze Progress & Calculate Metrics

<subagent name="product">
Perform comprehensive progress analysis.

Calculate:
- Feature completion percentages across all specs
- Development velocity metrics (tasks/day, features/week)
- Progress against current roadmap priorities
- Code quality metrics and test coverage
- Timeline projections and risk assessment

Generate comprehensive progress report.
</subagent>
</analyze_progress>

## Step 3: Strategic Recommendations

Based on progress analysis, product-agent provides:

### Current Status Summary
- Overall roadmap progress: [X]% complete
- Features in progress: [Count and status]
- Completed this period: [List]
- Blockers identified: [Any issues]

### Velocity & Quality Metrics
- Development velocity: [Tasks per day with AI assistance]
- Code quality indicators: [Test coverage, passing tests]
- AI efficiency multiplier: [Actual vs estimated time]

### Recommended Actions
#### Immediate (Today)
- [Specific next command to run]
- [Any urgent items to address]

#### This Week
- [Strategic priorities for the week]
- [Process improvements to consider]

### Roadmap Recommendations
- [Should priorities be updated?]
- [New features ready to start?]
- [Any timeline adjustments needed?]

## ✅ Progress Analysis Complete

**Next Action**: [Specific command recommendation]
**Alternative**: [If blocked or complete, what to do next]
