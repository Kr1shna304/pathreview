## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/146

**Issue title:** PII scrubber fails to redact parenthesized US phone numbers #146

**Tier:** [x] Tier 1  [ ] Tier 2  [ ] Tier 3

**Problem summary:**
The PII scrubber currently detects and redacts US phone numbers written with dashes (for example, `555-123-4567`), but it fails to recognize the common parenthesized format `(555) 123-4567`. As a result, these phone numbers are left unredacted and are not reported by the detection logic. The issue affects the phone number matching logic in the PII scrubber, and a successful fix will ensure both formats are detected and redacted consistently while allowing the existing tests to pass.


**Branch name:** `fix/146-parenthesized-phone-redaction`

**Setup confirmation:** [x] App runs locally at localhost:5173

**Cohort ledger:** [x] Issue added to cohort ledger






## Week 8 — Reproduction & solution planning

**Reproduction commit link:** https://github.com/Kr1shna304/pathreview/commit/c74b86a903bca441acd64f2fdd050de49129105f

**Reproduction summary:**
Reproduced the issue by running the existing PII scrubber unit tests in `tests/unit/test_pii_scrubber.py`. The tests confirmed that phone formats such as `(555) 123-4567` and `+1 555 123 4567` are not detected by `PIIScrubber.detect()` and are not replaced by `[REDACTED]` in `PIIScrubber.scrub()`, while other supported formats like `555-123-4567` and `555.123.4567` continue to work.

**PLAN.md link:** https://github.com/Kr1shna304/pathreview/blob/fix/146-parenthesized-phone-redaction/PLAN.md

**Walkthrough video (recommended):** https://drive.google.com/file/d/1Iac2YRsVF7IFfWeLPvEOG8TDyjpD6Y_s/view?usp=drive_link

**Blockers or open questions:**
Pre-commit hooks currently report existing ruff and mypy issues unrelated to the phone number reproduction.


## Week 9 — Solution building & PR submission

### Check-in 1 (mid-week)

**Current progress:**
[What have you implemented so far? Which sub-tasks from PLAN.md are done?]
I analyzed the existing regex patterns from Subtask 1 to identify why certain phone number formats were not being detected. After identifying the missing cases, I updated the phone_us pattern to support those formats and validated that the detection logic worked as expected. Before making changes, I also ran make check and discovered that two test functions were incomplete. I reviewed those tests and noted the additional work needed before completing the implementation.

**Next steps:**
Implement the remaining PLAN.md subtasks (Subtasks 3 and 4), complete the two incomplete test functions, add any required test cases for the updated phone number pattern, run the full test suite and validation checks, and verify that the changes do not introduce any regressions.

**Blockers:**
None

---

### Check-in 2 (end of week)

**PR link:** [link to your submitted pull request]

**Branch:** [the branch name you worked on, e.g. `fix/123-short-description`]

**What you built:**
[1–3 sentences summarizing what your fix does and how it works]

**Tests added or updated:**
[Which test files did you touch? What do they cover?]

**Self-review confirmation:** [ ] make check passes  [ ] make test-unit passes

**Draft PR feedback received from:** [name or Slack handle, or "none"]