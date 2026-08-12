# Unusable Coverage Forms — dev spec
Site: nomadinternet.com · Priority 4 · Urgent · Effort: Low (0.5-2 days)

## Problem
Critical forms (coverage check, qualification) are unusable because they lack visible input fields or labels, preventing user interaction.

## Evidence (from the live site)
> form: inputs=0 submit=CONTINUE labels=[]
> form: inputs=0 submit=CONTINUE labels=[]
> h1: What Best Describes Your Time on the Road?
> h1: How Do You Use the Internet at Home?
> form: inputs=0 submit=CONTINUE labels=[]

## Current state
h1: Let's Get You the Right Internet; cta: CONTINUE; notes: Coverage and qualification forms (e.g., 'What Best Describes Your Time on the Road?') render without visible input fields or labels, making them impossible to complete.

## Required change
h1: Let's Get You the Right Internet; cta: CONTINUE; notes: Implement visible input fields (e.g., address/ZIP) and labeled answer options (e.g., radio buttons) for all forms to enable user interaction.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Implement visible input fields (e.g., address/ZIP) and labeled answer options (e.g., radio buttons) for all forms to enable user interaction.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_form_interaction_friction_unusable` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 124,891 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
