# Inaccessible Controls — dev spec
Site: nomadinternet.com · Priority 10 · High · Effort: Low (0.5-2 days)

## Problem
5 of 46 buttons expose no text label, so screen readers and voice control cannot address them and the control is unusable.

## Evidence (from the live site)
> Measured on the live homepage: 5 of 46 <button> elements contain no text content and no aria-label.

## Current state
notes: 5 unlabelled interactive controls

## Required change
notes: Give every control a visible text label or an aria-label. WCAG 2.2 AA, success criterion 4.1.2 Name, Role, Value.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Give every control a visible text label or an aria-label. WCAG 2.2 AA, success criterion 4.1.2 Name, Role, Value.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_controls_without_accessible_names` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
