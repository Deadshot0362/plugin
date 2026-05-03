# Product Requirements Document (PRD): High-Conversion WordPress Popup Builder

## Problem Statement

WordPress site owners and marketers need a high-conversion, visually appealing way to build and display popups (such as exit-intent modals, slide-ins, and sticky bars) to capture leads, display offers, and drive sales. However, current solutions are problematic: they are either expensive SaaS products with high monthly fees, or they are bloated WordPress plugins that break under heavy caching (like WP Rocket), slow down the database by storing thousands of analytics events as post meta, or suffer from severe CSS conflicts where the active WordPress theme completely breaks the popup's layout.

## Solution

A professional-grade, highly performant WordPress plugin for building and managing popups. 
It features a modern, React-based drag-and-drop visual builder (powered by Craft.js) in the WordPress admin backend, delivering a premium, "SaaS-like" user experience. 
On the frontend, it solves the caching problem by utilizing a JavaScript-first trigger engine, pre-renders hidden HTML in the footer to ensure zero-latency display upon triggering (essential for exit-intent), and mounts the popup inside a Shadow DOM to guarantee total CSS isolation from the site's theme. Analytics and lead capture are handled via dedicated custom database tables and batched REST API requests to ensure enterprise-level performance and server stability on high-traffic websites.

## User Stories

1. As a marketer, I want to create a popup using a drag-and-drop visual interface, so that I can design beautiful lead magnets without writing code.
2. As a marketer, I want to add a countdown timer block to my popup, so that I can create urgency for a special offer.
3. As a marketer, I want to choose between Center Modal, Slide-in, or Sticky Bar formats, so that I can match the popup style to my specific campaign goals.
4. As a site visitor, I want the popup to display instantly when I move my mouse to close the tab, so that the experience feels seamless and responsive to my actions.
5. As a site owner, I want the popup rules to evaluate in the browser using JavaScript, so that my aggressive server-side caching (like Cloudflare or WP Rocket) doesn't break the trigger logic or show popups to the wrong people.
6. As a site owner, I want the popup's CSS to be isolated in a Shadow DOM, so that my WordPress theme's aggressive global CSS does not distort or break the popup's layout.
7. As a site owner, I want my popup analytics (impressions, conversions) saved in a custom, indexed database table, so that tracking data does not bloat my `wp_postmeta` table and crash my database.
8. As a developer, I want to batch analytics events and send them via the Beacon API on page unload, so that the server isn't overwhelmed by concurrent AJAX requests on high-traffic sites.
9. As a marketer, I want to capture leads (name and email) directly in the popup, so that I can grow my email list.
10. As a site owner, I want all captured leads to be saved safely into a local custom database table, so that no data is lost if a third-party API integration fails.
11. As a marketer, I want the ability to send captured leads via Webhooks to third-party services like Mailchimp or Zapier, so that my sales team can immediately act on new subscribers.
12. As an administrator, I want to manage all my popups through a standard WordPress Custom Post Type interface, so that I can use familiar WP features like user permissions, bulk actions, and draft statuses.

## Implementation Decisions

- **AdminBuilder (Frontend UI):** A React Single Page Application utilizing `Craft.js` will handle the drag-and-drop experience. It will be compiled via `@wordpress/scripts` to ensure compatibility with WordPress standards.
- **WPDataStore (Backend API):** A PHP backend utilizing a Custom Post Type (`popup`) for saving configuration (the React JSON state will be serialized in `post_meta`). Custom tables (`wp_popup_analytics` and `wp_popup_leads`) will be created upon plugin activation to handle high-volume data safely. Exposes secure REST API endpoints (`wp-json/popup/v1/track`) for data ingestion.
- **TriggerEngine (Frontend JS):** A Vanilla JS script injected into `wp_footer`. It evaluates rules client-side (e.g., scroll depth, exit intent) and emits a custom `popup_triggered` event. Bypasses PHP completely for rule evaluation.
- **ShadowRenderer (Frontend JS):** A Vanilla JS module that listens for the `popup_triggered` event and takes the pre-rendered HTML from the footer, injecting it into an isolated Shadow DOM to protect it from theme CSS conflicts.
- **AnalyticsBatcher (Frontend JS):** A client-side module that queues interaction events (views, clicks, closes) and flushes them to the REST API in batches, or via `navigator.sendBeacon()` upon page unload, to protect the server from DDOS-like traffic spikes.
- **Rendering Architecture:** Pre-rendering minified popup HTML in `wp_footer` (hidden) to ensure absolute zero latency, actively avoiding AJAX fetching at the moment of the trigger.
- **MVP Components:** The builder will strictly support Text, Image, Button, Lead Form, Countdown Timer, and Structural Container blocks for Version 1.0 to ensure a stable, rapid launch.

## Testing Decisions

- **Testing Philosophy:** A good test covers external behavior and edge cases without being tightly coupled to the implementation details. We will prioritize testing logic that executes under stress or specific conditions.
- **TriggerEngine:** Heavily unit tested using Jest. We will mock browser events (scroll, mouseout) to ensure complex rule combinations (e.g., exit intent + URL match) evaluate correctly without needing an actual DOM.
- **AnalyticsBatcher:** Unit tested to verify that events are correctly queued, deduplicated, and flushed under simulated page unload scenarios or timer intervals.
- **WPDataStore:** Integration tests for the REST endpoints to ensure they handle invalid payloads securely, sanitize inputs, and correctly insert records into the custom database tables.
- **AdminBuilder:** Functional UI tests using React Testing Library to verify that dragging blocks correctly updates the JSON state, and that the state deserializes back into the UI properly.

## Out of Scope

- Full-screen takeover popup formats.
- Dynamic WooCommerce product blocks or dynamic content pulling (e.g., "Related Posts").
- Complex visual assets like Lottie animations and video backgrounds.
- Native API integrations beyond basic Webhooks (e.g., native Hubspot, Salesforce, or ActiveCampaign integrations are deferred to V2).
- Advanced builder features like complex animation timelines or hover-state CSS editing.

## Further Notes

- The project relies on `@wordpress/scripts` to maintain alignment with the modern WordPress ecosystem, requiring a Node.js build step during development.
- Lead capture requires strict sanitization and WordPress Nonce validation (or equivalent secure token checking) on the REST API endpoint to prevent spam bot abuse.
