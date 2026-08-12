# Fragmented Plan Paths — dev spec
Site: nomadinternet.com · Priority 5 · High · Effort: Medium (2-5 days)

## Problem
Identical plan content across multiple URLs fragments the user journey and obscures the canonical next step.

## Evidence (from the live site)
> h1: Let's Get You the Right Internet
> h1: What Best Describes Your Time on the Road?
> h2: The Fastest Rural & On-the-Go Internet in the USA

## Current state
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE; notes: Identical plan content is accessible via `/pages/plans` and `/plans`, leading to fragmented user paths.

## Required change
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE; notes: Consolidate to a single canonical plans URL and implement 301 redirects for duplicates to unify the funnel.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Consolidate to a single canonical plans URL and implement 301 redirects for duplicates to unify the funnel.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_path_ambiguity` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
