---
name: bug-fix-workflow
description: Use this workflow when fixing bugs.
---

### Step 1: Prepare Context

1. State the expected and actual behavior; reproduce first if reproducible.
2. Trace from the symptom along call chains and data flows until the whole behavior is explained.
3. Understand the business goal of the code; confirm whether the current design is intentional.
4. Complexity triage: root cause clear and single, locally fixable, no side impact → skip Step 2/3, briefly state cause/fix/impact, go to Step 4; otherwise run the full flow.

### Step 2: Collect Causes Only, No Solution Yet

1. Find the direct cause of each bug (which code, under which condition, produces the symptom).
2. Dig from direct causes to root causes (wrong design assumption, unclear responsibility boundary, inconsistent data contract).
3. Record confirmed facts, inferences, and unverified assumptions separately; never treat an assumption as a conclusion.
4. For multiple bugs, judge holistically first: different symptoms of one root cause, or independent causes.

This step outputs cause conclusions only.

### Step 3: Decide the Fix from the Root Cause

1. Same root cause: one fix covering all symptoms. Different causes: one fix per cause, none masking another.
2. A local patch truly resolves the root cause → minimal fix. A patch only hides the symptom and similar bugs will recur → architectural problem: give evidence and an overall plan, do not disguise it as a local fix; enter Step 4 after the user confirms the plan.
3. Do not expand refactoring without evidence.
4. Before acting, briefly state to the user: cause, approach, impact.

### Step 4: Fix and Verify

1. Change only what relates to the root cause; no unrelated edits.
2. Verify: the reproduction case is gone, no obvious regression in related features, edge cases (null values, exception branches) hold.
3. Report verified results and reasoning-based conclusions separately; label anything unverified.
4. Verification fails → return to Step 2 and re-judge the cause; do not keep patching.

### Step 5: Review

1. Is there a smaller, more maintainable solution?
2. Does this bug expose a design-level deficiency?
3. Conclusions are suggestions only — implement after user confirmation, never refactor beyond this fix on your own.
