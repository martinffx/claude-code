---
description: Implement feature following TDD and architectural standards
argument-hint: <feature_name> [task_id]
---

# Implementation: $FEATURE_NAME

<load_progress>
## Step 1: Load Current Progress

<subagent name="context">
Retrieve task list and current status.

Load tasks.md and status.md to identify next task.
</subagent>
</load_progress>

<implement_tdd>
## Step 2: Implement with TDD

<subagent name="coder">
Implement using stub-driven TDD per docs/standards/coding.md:

Step 1: Create stub (coding.md#stub-patterns)
- Generate method signatures with "Not Implemented" errors
- Establish dependency structure

Step 2: Write test (coding.md#test-writing)
- Test against stub (expect "Not Implemented")
- Document expected behavior in test

Step 3: Implement (coding.md#implementation)
- Replace stub with working code
- Make tests pass

Follow Entity → Repository → Service → Router order.
</subagent>
</implement_tdd>

<update_status>
## Step 3: Update Task Status

<subagent name="scaffold">
Update progress tracking.

Update status.md with completed task and next action.
</subagent>
</update_status>

## ✅ Task Complete

Implementation completed using TDD:
- Tests written first and passing
- Code follows architectural standards
- Progress tracking updated
- Ready for next task

**Next options:**
1. Continue: `/spec:implement $FEATURE_NAME`
2. Check progress: `/spec:progress $FEATURE_NAME`
3. Specific task: `/spec:implement $FEATURE_NAME [task_id]`
