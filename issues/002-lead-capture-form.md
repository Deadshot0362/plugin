## Parent PRD

`issues/prd.md`

## What to build

Implement the end-to-end lead capture pipeline. This allows users to add a signup form to their popups and store the submitted data safely in the WordPress database.

Key deliverables:
- Creation of the `wp_popup_leads` custom database table on plugin activation.
- A "Lead Form" block in the React/Craft.js builder with fields for Name and Email.
- Frontend JS logic to handle form submission, including basic validation and AJAX/REST dispatch.
- A secure WordPress REST API endpoint (`wp-json/popup/v1/lead`) to ingest submissions and save them to the `wp_popup_leads` table.

## Acceptance criteria

- [ ] `wp_popup_leads` table is successfully created in the database.
- [ ] Users can drag the "Lead Form" block into a popup and save it.
- [ ] Submitting the form on the frontend results in a new row in the `wp_popup_leads` table.
- [ ] The submission process is secure, using nonces or secure tokens to prevent spam.

## Blocked by

- Blocked by `issues/001-hello-world-text-popup.md`

## User stories addressed

- User story 9
- User story 10
