# No Responsive Viewport — dev spec
Site: nomadinternet.com · Priority 3 · Urgent · Effort: Medium (2-5 days)

## Problem
Without a viewport meta tag mobile browsers render the desktop layout scaled down, making every tap target too small.

## Evidence (from the live site)
> Measured on the mobile render: no <meta name="viewport"> present.

## Current state
notes: no viewport meta tag

## Required change
notes: Add <meta name="viewport" content="width=device-width, initial-scale=1">

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add <meta name="viewport" content="width=device-width, initial-scale=1">
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_no_responsive_viewport_declared` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 124,891 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
