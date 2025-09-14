---
description: Update product roadmap with next priorities
argument-hint: [update]
---

# Update Roadmap

<analyze_current_state>
## Step 1: Analyze Current State

<subagent name="context">
Gather current project state.

Retrieve:
- Current roadmap priorities from `docs/product/roadmap.md`
- Feature completion status from `docs/specs/*/status.md`
- Available features from `docs/product/product.md`

Load and analyze current state.
</subagent>
</analyze_current_state>

<calculate_metrics>
## Step 2: Calculate Progress Metrics

<subagent name="product">
Analyze progress and generate recommendations.

Calculate:
- Feature completion percentages
- Development velocity metrics  
- Timeline assessments
- Priority recommendations

Provide strategic recommendations.
</subagent>
</calculate_metrics>

## Step 3: Priority Interview

Based on current progress analysis, confirm your next priorities:

### Current Features Status
- [Feature status from product-agent analysis]

### Available Features  
- [Features from product.md not yet started]

### Recommended Next 3 Priorities
1. **[Product-agent recommendation 1]** - [Reasoning]
2. **[Product-agent recommendation 2]** - [Reasoning]  
3. **[Product-agent recommendation 3]** - [Reasoning]

**Confirm or adjust these priorities:** [Waiting for user input]

<update_roadmap_file>
## Step 4: Update Roadmap File

<subagent name="scaffold">
Update `docs/product/roadmap.md` with new priorities.

Update roadmap file with confirmed priorities and current status.
</subagent>
</update_roadmap_file>

## ✅ Roadmap Updated

### Summary:
- Progress analysis completed
- New priorities confirmed
- Roadmap file updated

### Next Actions:
1. Continue active feature: `/spec:implement [current-feature]`
2. Start next priority: `/spec:create [next-feature]`
3. Check overall progress: `/product:progress`
