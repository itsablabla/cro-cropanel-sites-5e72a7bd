# Duplicate CONTINUE Buttons — dev spec
Site: nomadinternet.com · Priority 6 · High · Effort: Low (0.5-2 days)

## Problem
Multiple identical 'CONTINUE' buttons on the same page, without distinguishing labels, create confusion and force users to guess the correct action.

## Evidence (from the live site)
> form: inputs=0 submit=CONTINUE labels=[]
> form: inputs=0 submit=CONTINUE labels=[]

## Current state
h1: Let's Get You the Right Internet; cta: CONTINUE; notes: Multiple pages display two identical 'CONTINUE' buttons within forms, lacking distinguishing labels, causing user confusion.

## Required change
h1: Let's Get You the Right Internet; cta: CONTINUE; notes: Consolidate duplicate 'CONTINUE' forms or clearly label each button with its specific purpose (e.g., 'Check Home Coverage').

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Consolidate duplicate 'CONTINUE' forms or clearly label each button with its specific purpose (e.g., 'Check Home Coverage').
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_form_interaction_friction_duplicate_continue` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
