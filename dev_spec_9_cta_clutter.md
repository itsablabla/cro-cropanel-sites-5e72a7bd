# Confusing CTA Options — dev spec
Site: nomadinternet.com · Priority 9 · Medium · Effort: Medium (2-5 days)

## Problem
Multiple equally prominent calls to action on each page dilute user focus and create ambiguity about the intended next step.

## Evidence (from the live site)
> ctas: CHECK COVERAGE | CHECK IF IT WORKS AT MY ADDRESS | SEE MY OPTIONS | GET STARTED | START CHAT | SEE WHAT I QUALIFY FOR | CHECK MY COVERAGE
> ctas: CHECK COVERAGE | SEE WHAT I QUALIFY FOR | CHECK MY COVERAGE

## Current state
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE | GET STARTED | START CHAT; notes: Multiple CTAs (e.g., 'CHECK COVERAGE', 'GET STARTED', 'START CHAT') appear with similar prominence, diluting user focus.

## Required change
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE; notes: Designate one clear primary CTA per page and visually demote secondary actions to improve focus.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Designate one clear primary CTA per page and visually demote secondary actions to improve focus.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_cta_clutter` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
