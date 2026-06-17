# Contribution 1: Extend RFECV attributes to indicate order of feature elimination

**Contribution Number:** 1
**Student:** Gunakarthik Naidu Lanka
**Issue:** https://github.com/scikit-learn/scikit-learn/issues/13756
**Fork:** https://github.com/Gunakarthik1/scikit-learn
**Status:** Phase II Complete

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

Set up the official scikit-learn dev container (.devcontainer/) in VS Code/Cursor with Docker Desktop running. The container's setup.sh installs micromamba and creates the sklearn-dev environment (Python 3.14). Two issues encountered: (1) the initial container build failed once and required Retry; (2) after creating the env, import numpy aborted with a libblis error (Default MC is non-multiple of MR) on aarch64 (Apple Silicon). Fixed by swapping the BLAS backend from blis to openblas: micromamba install -n sklearn-dev "libblas=*=*openblas" --yes. After that, built scikit-learn in editable mode with pip install --editable . --no-build-isolation, which succeeded.

### Steps to Reproduce

1. In the built sklearn-dev environment, create a script that fits RFECV on a toy dataset using make_classification, SVC, and RFECV from sklearn.
2. Run python repro.py.
3. Expected: an attribute exposing which feature was eliminated at each step.
4. Actual: fitted attributes are only ['classes_', 'cv_results_', 'estimator_', 'n_features_', 'n_features_in_', 'ranking_', 'support_'] — no per-step elimination order is available. Confirmed consistent across two runs.

### Reproduction Evidence

- **Commit showing reproduction / branch link:** https://github.com/Gunakarthik1/scikit-learn/tree/fix-issue-13756
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

**Understand:** RFECV performs recursive feature elimination but never records the order in which features were dropped. Users can see final rankings (ranking_) but not the step-by-step elimination sequence.

**Match:** The RFECV.fit() method in sklearn/feature_selection/_rfe.py already iterates through elimination rounds and builds up ranking_. The new attribute can be populated inside this same loop, following the existing fitted-attribute convention (trailing underscore).

**Plan:**
1. In sklearn/feature_selection/_rfe.py, add a new fitted attribute (e.g. elimination_order_) to the RFECV class.
2. Populate it inside the existing elimination loop in fit(), appending the index of each feature as it's removed.
3. Document the attribute in the class docstring.
4. Add a unit test in sklearn/feature_selection/tests/test_rfe.py.

**Implement:** To be completed in Phase III on branch fix-issue-13756.

**Review:** Self-review against scikit-learn's CONTRIBUTING.md and docstring/attribute conventions before opening a PR.

**Evaluate:** Add a unit test asserting elimination_order_ has the expected length and contents; run the existing RFE/RFECV test suite to confirm no regressions.

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
