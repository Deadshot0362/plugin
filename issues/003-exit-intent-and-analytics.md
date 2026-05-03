## Parent PRD

`issues/prd.md`

## What to build

Implement the behavior tracking and analytics pipeline. This includes the high-performance trigger logic and the batched data ingestion system.

Key deliverables:
- Creation of the `wp_popup_analytics` custom database table.
- A "Trigger" setting in the React builder to select "Exit Intent".
- Frontend JS logic to detect exit intent behavior (mouse movement outside the viewport).
- The `AnalyticsBatcher` JS module to queue impression/close events.
- A REST API endpoint (`wp-json/popup/v1/track`) to ingest batched analytics using the Beacon API on page unload.

## Acceptance criteria

- [ ] `wp_popup_analytics` table is successfully created.
- [ ] Setting a popup to "Exit Intent" correctly triggers the display on the frontend when the user attempts to close the tab.
- [ ] Impressions are correctly recorded in the custom table without using `admin-ajax.php`.
- [ ] Analytics requests use `navigator.sendBeacon()` or batched REST requests to minimize server load.

## Blocked by

- Blocked by `issues/001-hello-world-text-popup.md`

## User stories addressed

- User story 5
- User story 7
- User story 8
