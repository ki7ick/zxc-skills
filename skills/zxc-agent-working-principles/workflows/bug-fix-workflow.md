---
name: bug-fix-workflow
description: Use this workflow when fixing bugs.
---

Fix bugs should follow the steps below, and show current and next step number title in progressing.

### Step 1: Prepare Context

1. Trace from the symptom along call chains and data flows until the whole behavior is explained.
2. Understand the business goal of the code;

### Step 2: Collect Causes

1. Find the direct cause and root cause of each bug.
2. Summarize all the causes.

### Step 3: Think and give fixes

1. Those bugs's root causes are same or different?
2. Need a patch or a architectural refactor?
3. Give fixes.

### Step 4: Fix and Verify

1. Fix bugs by fixes that provided by Step 3.
2. Verify: run code test cases or external tools(like chrome browser, verify as real user).
3. If verification fails => Recursion call Step 2-Step 3 in flexibly.

### Step 5: Review

1. Is there a smaller, more maintainable solution?
2. Does this bug expose a design-level deficiency?
3. Conclusions are suggestions only — implement after user confirmation, never refactor beyond this fix on your own.
