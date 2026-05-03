## Parent PRD

`issues/prd.md`

## What to build

Establish the fundamental end-to-end "tracer bullet" for the plugin. This includes setting up the core WordPress infrastructure and the React build pipeline to deliver a simple text-based popup to the frontend.

Key deliverables:
- WordPress plugin skeleton and `@wordpress/scripts` configuration.
- Registration of the `popup` Custom Post Type (CPT).
- A basic React/Craft.js admin interface with a single "Text" block.
- Serialization of the Craft.js node tree into JSON and saving it to `post_meta`.
- A PHP frontend renderer that outputs the saved text as a hidden HTML block in the `wp_footer`.
- A lightweight Vanilla JS trigger engine that fires after a default 2-second timeout and injects the text into a Shadow DOM center modal.

## Acceptance criteria

- [ ] Plugin activates without errors and creates the `popup` CPT.
- [ ] `npm run build` successfully compiles the React admin builder.
- [ ] Users can edit a popup, type text, and save the post.
- [ ] The saved text appears in a Shadow DOM modal on the frontend after 2 seconds.
- [ ] Popup styles are isolated and not affected by the active theme's CSS.

## Blocked by

None - can start immediately

## User stories addressed

- User story 1
- User story 4
- User story 6
- User story 12
