## Parent PRD

`issues/prd.md`

## What to build

Implement the Slide-in format and the external data delivery system via Webhooks.

Key deliverables:
- A "Format" setting for "Slide-in" (Bottom Right/Left) in the React builder.
- Animation logic for the slide-in effect on the frontend.
- A "Webhook" settings panel in the admin to configure a target URL for lead data.
- Backend PHP logic to dispatch lead data to the configured Webhook URL whenever a lead is captured (integration with `issues/002`).

## Acceptance criteria

- [ ] Popups correctly slide in from the corners of the screen when configured as "Slide-in".
- [ ] Submitting a lead successfully triggers an outbound POST request to the configured Webhook URL.
- [ ] Webhook payloads contain the lead's Name, Email, and the ID of the popup that triggered it.

## Blocked by

- Blocked by `issues/002-lead-capture-form.md`

## User stories addressed

- User story 3
- User story 11
