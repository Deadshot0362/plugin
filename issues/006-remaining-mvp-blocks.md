## Parent PRD

`issues/prd.md`

## What to build

Flesh out the builder's structural and media capabilities by adding the remaining core blocks.

Key deliverables:
- "Image" block: Integration with the WordPress Media Library to select and display images.
- "Button" block: Settings for button text, background/text colors, and action (Redirect to URL or Close Popup).
- "Container" block: A structural wrapper that allows for column layouts or background styling within the popup.
- PHP renderers for all three blocks to ensure they appear correctly inside the Shadow DOM.

## Acceptance criteria

- [ ] Users can upload or select images from the WP Media Library within the builder.
- [ ] Buttons can be configured to either redirect the user or dismiss the popup.
- [ ] Complex layouts (e.g., text on the left, image on the right) are possible using the Container block.
- [ ] Blocks are fully responsive and look good on mobile devices.

## Blocked by

- Blocked by `issues/001-hello-world-text-popup.md`

## User stories addressed

- User story 1
