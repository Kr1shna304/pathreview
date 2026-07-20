## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/146

**Issue title:** PII scrubber fails to redact parenthesized US phone numbers #146

**Tier:** [x] Tier 1  [ ] Tier 2  [ ] Tier 3

**Problem summary:**
The PII scrubber currently detects and redacts US phone numbers written with dashes (for example, `555-123-4567`), but it fails to recognize the common parenthesized format `(555) 123-4567`. As a result, these phone numbers are left unredacted and are not reported by the detection logic. The issue affects the phone number matching logic in the PII scrubber, and a successful fix will ensure both formats are detected and redacted consistently while allowing the existing tests to pass.


**Branch name:** `fix/146-parenthesized-phone-redaction`

**Setup confirmation:** [x] App runs locally at localhost:5173

**Cohort ledger:** [x] Issue added to cohort ledger