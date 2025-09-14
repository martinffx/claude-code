---
description: Create feature specification through structured requirements gathering
argument-hint: <feature_name>
---

# Create Feature Spec: $FEATURE_NAME

<requirements_gathering>
## Step 1: Gather Requirements

I'll ask you questions to understand this feature. Please provide specific answers.

### User Story
**Format:** As a [user type], I want to [action] so that [benefit]
**Example:** "As a customer, I want to reset password so that I can regain access"

Your user story for $FEATURE_NAME:

[Wait for response]

### Acceptance Criteria
**List 3-5 specific, testable conditions for success:**
**Example:**
- User receives email within 60 seconds
- Link expires after 24 hours
- Password meets security requirements

Your criteria:

[Wait for response]

### Business Rules
**What constraints or validation rules apply?**
**Example:** "Max 3 reset attempts per day", "Only verified emails"

Your rules:

[Wait for response]

### Scope
**What's included?** (list features)
**What's excluded?** (explicitly out of scope)

[Wait for response]

### Output: `docs/specs/$FEATURE_NAME/requirements.json`
```json
{
  "raw_user_story": "[user's answer]",
  "raw_criteria": "[user's answer]",
  "raw_rules": "[user's answer]",
  "raw_scope": "[user's answer]"
}
```
</requirements_gathering>

## Step 2: Load Project Context

<subagent name="context">
Using context to retrieve relevant project information...

First read: docs/specs/$FEATURE_NAME/requirements.json

Use the sequential thinking tool to analyze the following files and extract relavent context:
- docs/product/product.md → vision
- docs/specs/*/ → existing features
- docs/standards/ → patterns

Please provide context on existing relavent code and features in the code base.

### Output: `docs/specs/$FEATURE_NAME/context.json`

```json
{
  "product_vision": "...",
  "existing_features": ["auth", "profile"],
  "architecture": {...}
}
```
</subagent>

## Step 3: Requirements Analyst

<subagent name="analyst">

Use the sequential thinking tool to combine `docs/specs/$FEATURE_NAME/requirements.json` + `docs/specs/$FEATURE_NAME/context.json`:
- Parse raw user story into proper format
- Structure acceptance criteria as testable items
- Align with existing patterns from context
- Check for conflicts with existing features

### Output: `docs/specs/$FEATURE_NAME/spec.json`
```json
{
  "feature": "$FEATURE_NAME",
  "user_story": "As a...",
  "acceptance_criteria": [
    "GIVEN... WHEN... THEN...",
    "User can..."
  ],
  "business_rules": ["..."],
  "scope": {
    "included": ["..."],
    "excluded": ["..."]
  },
  "aligns_with": "product_vision",
  "dependencies": ["auth"],
  "technical_details": [{...}]
}
```

</subagent>

## Step 4: Create Specification Files

<subagent name="scaffold">
Using scaffold to generate specification files...

Read: `docs/specs/$FEATURE_NAME/spec.json`

template: `~/.claude/docs/templates/specs/spec.md`

Files created in `docs/specs/$FEATURE_NAME/`:
- `spec.md` - Complete feature specification
- `spec-lite.md` - Condensed version for AI context

</subagent>

## ✅ Specification Complete

Created complete feature specification with:
- Structured requirements from analyst-agent
- Proper file organization from scaffold-agent
- Ready for technical design phase

**Next steps:**
1. Review the specification
2. Create technical design: `/spec:design $FEATURE_NAME`
3. Or jump to implementation: `/spec:plan $FEATURE_NAME`
