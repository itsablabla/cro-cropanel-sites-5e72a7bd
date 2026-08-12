# Inefficient Funnel Order — dev spec
Site: nomadinternet.com · Priority 8 · Medium · Effort: High (5+ days)

## Problem
Requiring a coverage check before presenting plan options adds an unnecessary step, potentially increasing drop-off.

## Evidence (from the live site)
> ctas: CHECK COVERAGE | CHECK IF IT WORKS AT MY ADDRESS | SEE MY OPTIONS | GET STARTED | START CHAT | SEE WHAT I QUALIFY FOR | CHECK MY COVERAGE
> ctas: CHECK COVERAGE | SEE WHAT I QUALIFY FOR | CHECK MY COVERAGE

## Current state
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE; notes: Primary CTAs on homepage and plans pages direct users to a coverage check before displaying plan options.

## Required change
h1: Let's Get You the Right Internet; cta: SEE PLANS; notes: Reorder the funnel to present plan options first, then integrate coverage verification as a subsequent confirmation step.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Reorder the funnel to present plan options first, then integrate coverage verification as a subsequent confirmation step.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_funnel_order_inefficiency` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
