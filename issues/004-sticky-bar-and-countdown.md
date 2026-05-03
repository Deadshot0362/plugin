## Parent PRD

`issues/prd.md`

## What to build

Implement additional layout formats and the dynamic countdown timer component. This allows users to create urgency-driven popups in non-intrusive formats.

Key deliverables:
- A "Format" setting in the React builder for "Sticky Bar" (Top/Bottom).
- The "Countdown Timer" block in the Craft.js builder with settings for target date/time.
- Frontend JS logic to handle the live countdown timer ticking.
- Positioning logic in the `ShadowRenderer` to correctly anchor sticky bars to the top or bottom of the viewport.

## Acceptance criteria

- [ ] Users can toggle between Modal and Sticky Bar formats in the admin.
- [ ] Sticky bars appear correctly anchored to the top or bottom of the screen on the frontend.
- [ ] The countdown timer block correctly calculates and displays remaining time in real-time.
- [ ] Sticky bars do not overlap with common WordPress admin bar or site headers (CSS adjustment).

## Blocked by

- Blocked by `issues/001-hello-world-text-popup.md`

## User stories addressed

- User story 2
- User story 3
