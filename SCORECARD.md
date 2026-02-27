# Scorecard

> Score a repo before remediation. Fill this out first, then use SHIP_GATE.md to fix.

**Repo:** a11y-evidence-engine
**Date:** 2026-02-27
**Type tags:** `[all]` `[npm]` `[cli]`

## Pre-Remediation Assessment

| Category | Score | Notes |
|----------|-------|-------|
| A. Security | 4/10 | SECURITY.md template only, no threat model in README |
| B. Error Handling | 5/10 | Exit codes present, but errors are raw strings — no structured codes |
| C. Operator Docs | 6/10 | README good, CHANGELOG empty, LICENSE present |
| D. Shipping Hygiene | 5/10 | CI has test+lint, but no verify script, no dep audit, no coverage |
| E. Identity (soft) | 10/10 | Logo, translations, landing page, GitHub metadata |
| **Overall** | **30/50** | |

## Key Gaps

1. Error messages are raw strings — no structured error shape (Section B)
2. SECURITY.md is template only — no real data scope (Section A)
3. No verify script (Section D)
4. CHANGELOG.md empty (Section C)
5. No Codecov upload or dep audit in CI (Section D)

## Post-Remediation

| Category | Before | After |
|----------|--------|-------|
| A. Security | 4/10 | 10/10 |
| B. Error Handling | 5/10 | 10/10 |
| C. Operator Docs | 6/10 | 10/10 |
| D. Shipping Hygiene | 5/10 | 10/10 |
| E. Identity (soft) | 10/10 | 10/10 |
| **Overall** | 30/50 | **50/50** |
