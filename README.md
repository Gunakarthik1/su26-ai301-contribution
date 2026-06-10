# Contribution 1: Extend RFECV attributes to indicate order of feature elimination

**Contribution Number:** 1
**Student:** Gunakarthik Naidu Lanka
**Issue:** https://github.com/scikit-learn/scikit-learn/issues/13756
**Fork:** https://github.com/Gunakarthik1/scikit-learn
**Status:** Phase I Complete

---

## Why I Chose This Issue

I chose this issue because it involves scikit-learn, a Python machine learning 
library that aligns directly with my Python background. The fix is well-scoped: 
adding a new attribute to the RFECV class that tracks which feature was eliminated 
at each step of recursive feature elimination. Currently, RFECV shows scores for 
each step but does not expose which specific feature was removed, making it 
difficult for users to interpret and verify results.

I chose this issue specifically because the maintainer has explicitly welcomed a 
pull request twice, confirming it is active and claimable. The work is contained 
within one class in the feature selection module, which makes it approachable for 
a first contribution. I want to learn how scikit-learn handles class attributes 
and how open source contributions work in a large, well-maintained Python project.

---

## Understanding the Issue

### Problem Description

`sklearn.feature_selection.RFECV` performs recursive feature elimination with 
cross-validation. It currently exposes scores at each elimination step, but does 
not tell the user which feature was eliminated at each step. This missing 
information makes it hard to trace and verify the elimination process.

### Expected Behavior

After fitting RFECV, users should be able to access a new attribute (e.g. 
`ranking_order_` or `elimination_order_`) that lists which feature was removed 
at each step of the recursive elimination process.

### Current Behavior

Currently RFECV only exposes `cv_results_` scores per step, with no way to know 
which feature was eliminated at each step.

### Affected Components

`sklearn/feature_selection/_rfe.py` — specifically the `RFECV` class.

---

## Reproduction Process

### Environment Setup

[To be filled in Phase II]

### Steps to Reproduce

1. [Step 1]
2. [Step 2]
3. [Observed result]

### Reproduction Evidence

- **Commit showing reproduction:** [Link to commit in your fork]
- **Screenshots/logs:** [If applicable]
- **My findings:** [What you discovered during reproduction]

---

## Solution Approach

### Analysis

[To be filled in Phase II]

### Proposed Solution

[To be filled in Phase II]

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** [Restate the problem]

**Match:** [What similar patterns/solutions exist in the codebase?]

**Plan:** [Step-by-step implementation plan]
1. [Modify file X to do Y]
2. [Add function Z]
3. [Update tests]

**Implement:** [Link to your branch/commits as you work]

**Review:** [Self-review checklist - does it follow the project's contribution guidelines?]

**Evaluate:** [How will you verify it works?]

---

## Testing Strategy

### Unit Tests

- [ ] Test case 1: [Description]
- [ ] Test case 2: [Description]
- [ ] Test case 3: [Description]

### Integration Tests

- [ ] Integration scenario 1
- [ ] Integration scenario 2

### Manual Testing

[What you tested manually and results]

---

## Implementation Notes

### Week 1 Progress

Selected issue and set up contribution README. Forked scikit-learn repository.

### Week [Y] Progress

[Continue documenting as you work]

### Code Changes

- **Files modified:** [List]
- **Key commits:** [Links to important commits]
- **Approach decisions:** [Why you chose certain approaches]

---

## Pull Request

**PR Link:** [GitHub PR URL when submitted]

**PR Description:** [Draft or final PR description]

**Maintainer Feedback:**
- [Date]: [Summary of feedback received]
- [Date]: [How you addressed it]

**Status:** [Awaiting review / Iterating / Approved / Merged]

---

## Learnings & Reflections

### Technical Skills Gained

[What you learned technically]

### Challenges Overcome

[What was hard and how you solved it]

### What I'd Do Differently Next Time

[Reflection on your process]

---

## Resources Used

- https://github.com/scikit-learn/scikit-learn/issues/13756
- https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.RFECV.html
- https://github.com/scikit-learn/scikit-learn/blob/main/CONTRIBUTING.md
