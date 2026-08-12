# Weak Security Headers — dev spec
Site: nomadinternet.com · Priority 1 · Medium · Effort: Medium (2-5 days)

## Problem
3 of 6 standard security headers are absent, which weakens protection against XSS, clickjacking and downgrade attacks.

## Evidence (from the live site)
> Measured on the live origin: missing X-Frame-Options, Referrer-Policy, Permissions-Policy.

## Current state
notes: missing: X-Frame-Options, Referrer-Policy, Permissions-Policy

## Required change
notes: Add the missing headers at the CDN or web-server layer; HSTS and X-Content-Type-Options are one-line changes.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add the missing headers at the CDN or web-server layer; HSTS and X-Content-Type-Options are one-line changes.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_missing_security_headers` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
