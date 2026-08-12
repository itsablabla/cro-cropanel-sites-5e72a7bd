# Missing Trust Signals — dev spec
Site: nomadinternet.com · Priority 7 · High · Effort: Medium (2-5 days)

## Problem
Key pages lack visible social proof (review context), explicit guarantees, or security badges, undermining user confidence at critical decision points.

## Evidence (from the live site)
> 4.3 stars from 9,200+ Google reviews
> SHOP WITH CONFIDENCE
> CHECK COVERAGE
> SEE WHAT I QUALIFY FOR

## Current state
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE; notes: Homepage displays '4.3 stars from 9,200+ Google reviews' without context. Key pages lack explicit guarantees or security badges near CTAs like 'CHECK COVERAGE'.

## Required change
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE; notes: Enhance review context, add clear money-back guarantees on relevant pages, and display recognizable security badges near pricing and CTAs.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Enhance review context, add clear money-back guarantees on relevant pages, and display recognizable security badges near pricing and CTAs.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_trust_deficit` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
