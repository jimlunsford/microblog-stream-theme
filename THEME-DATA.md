# Theme Data Boundary

Microblog Stream v2.1.4 is a code-free Bonumark Stream theme targeting v0.7.2 and v0.8.1 using Declarative Layout Schema 1 on selected public surfaces.

Core prepares application data, validates theme composition, and renders all public component markup. The theme declares safe composition through JSON, styles the core-owned markup through CSS, and reads settings declared in `theme.json`.

Allowed theme files:

- `theme.json`
- `README.md`
- `layouts/*.json` files declared by `theme.json`
- CSS files
- image files
- font files, if declared
- screenshot files

Not allowed:

- PHP
- JavaScript
- HTML templates
- route handlers
- app helpers
- database logic
- permission logic


## v2.1.4 adjustment

Adds presentation for the core Following and Conversation template, including remote identities, disclosure controls, media, interaction states, deleted content, and errors. Adds containment for the core federated-comment wrapper. The remote reply form keeps the core Stream composer contract. Themes do not declare a new Following layout surface or an invented ActivityPub support flag.

All existing layout JSON, settings, and capability declarations are preserved. The minimum core marker is narrowed to v0.7.2; v0.8.1 is the federation presentation target. Source/static validation is complete, with native Theme Health and browser acceptance still pending as described in README.md.

No PHP, JavaScript, HTML templates, routes, forms, account data, or federation logic are included in the theme.

## v2.1.3 adjustment

This micro-pass changes only CSS for narrow single-post reader actions. The core-owned Likes, Comments, Back to stream, and Post options controls keep their markup, behavior, permissions, accessibility attributes, and data contracts. On small screens, the theme arranges those existing controls into a stable two-column presentation so the overflow menu no longer drops onto an accidental row by itself.

Feed-card actions are unchanged. The validated `profile`, `stream-card`, and `home` JSON documents are unchanged from v2.1.2, and Site Header remains on the legacy core composition.

No application behavior or component ownership changed.

## v2.1.2 adjustment

This is a presentation-only density and finish pass. The validated `profile`, `stream-card`, and `home` JSON documents are unchanged from v2.1.1, and Site Header remains on the legacy core composition. CSS tightens the existing Profile intro overlap, mobile identity spacing, supporting-rail padding, Featured spacing, Stream Card rhythm, action-control sizing, compact link-preview dimensions, and mobile comment-form spacing.

The Profile photo component is not altered. Bonumark Stream v0.5.120 core supplies responsive Profile photo markup with lazy loading and low fetch priority. The blank image surfaces visible in some automated full-page mobile captures are consistent with off-viewport lazy loading, not a theme rule that hides the photos. The theme therefore preserves core media loading behavior rather than forcing eager gallery downloads.

No data, media, behavior, accessibility, interaction, or application ownership changed.


## v2.1.1 adjustment

The Profile composition now wraps the already registered core `profile.cover`, `profile.avatar`, and `profile.identity` components inside a new `microblog-profile-intro` group. This gives CSS a safe layout hook for visually joining cover and identity without changing any core component markup or putting Profile text inside the cover component.

The supporting `microblog-profile-rail` still contains the core-owned Now, Interests, Links, and Details components, but v2.1.1 styles the rail as one presentation surface with internal separators. Featured and Photos remain independent full-width components and receive stronger visual hierarchy.

On narrow screens, the declarative Stream Card root becomes a full-width reading composition. The core avatar component is positioned as the visual anchor for the header row, while body, link preview, media, and actions use the full card width. Public link previews keep their core markup and data but use a compact thumbnail-and-copy presentation on mobile.

No component ownership changed. Bonumark Stream still owns Profile data, link-preview generation, media markup, stream actions, comments, accessibility behavior, and all application logic.


## v2.1.0 adjustment

The theme now opts into Bonumark Stream Declarative Layout Schema 1 for three surfaces:

- `profile`
- `stream-card`
- `home`

The Profile layout composes core-owned cover, avatar, identity, About, Featured, Photos, Now, Interests, Links, and Details components into a stronger desktop hierarchy while collapsing safely on mobile. The Stream Card layout makes the existing avatar-left/content-right structure explicit. The Home layout separates publishing and timeline zones without taking ownership of the composer, pinned posts, feed, or pagination.

The `site-header` surface is intentionally not declared. Microblog Stream continues through the legacy core Site Header composition because that core path exposes the theme's existing `show_status_chip`, `status_label`, and `show_post_count` presentation settings. This is deliberate partial adoption, not a missing migration.

The layout files contain only validated `group` and `component` nodes. They do not contain HTML, executable code, conditions, expressions, routes, database access, or application logic.


## v2.0.12 adjustment

The theme now polishes the core-owned Profile editor used by Bonumark Stream v0.5.87. This pass improves field sizing, helper-text readability, spacing, action-button treatment, upload controls, the Featured Work editor, the Profile Photos editor, the Save Profile area, and the Profile portability panel. The theme does not change Profile storage, uploads, metadata, export contents, permissions, or any Bonumark application behavior.

## v2.0.11 adjustment

The theme now styles the current core-owned Profile identity contract introduced across Bonumark Stream v0.5.80 through v0.5.87. This includes cover and identity panels, About, Now, Interests, Links, optional Details, Featured work, Profile Photos, Profile editor controls, and the Profile portability panel. The theme also top-aligns the public shell so short pages do not inherit the large empty vertical gap that older flex-shell styling could create.

The theme does not store Profile data, resolve Featured items, upload or delete Profile photos, generate metadata, create exports, control privacy, add routes, or own the full-image viewer. It only styles stable core markup. The obsolete `profile_layouts` capability declaration has been removed because Bonumark core does not define a universal Profile layout selector.

## v2.0.10 adjustment

The theme now styles the core-owned unified composer menu, Advanced options panel, front-end Quick edit form, expanded Post options menu, and recoverable Move to trash action used by Bonumark Stream v0.5.49. Bonumark Stream core still owns draft creation, full-editor continuation, metadata processing, revisions, permission checks, CSRF protection, conflict detection, post updates, trash storage, restoration, and permanent deletion.

## v2.0.9 adjustment

The theme now styles the core-owned multi-photo composer preview introduced in Bonumark Stream v0.5.44. It no longer applies the older one-file flex row or fixed 64-pixel thumbnail rules to the new gallery preview markup. File selection, preview creation, ordering, removal, upload validation, and publishing remain core behavior.

## v2.0.8 adjustment

The theme now styles the core-owned Local Places composer, add-place dialog, nearby results, selected-place state, and public location details introduced in Bonumark Stream v0.5.36 and newer. The theme does not request location access, save coordinates, search places, attach places to posts, or publish location data.

## v2.0.7 adjustment

The theme tightens spacing in the core-owned Post options menu so Edit and Pin to Stream / Unpin from Stream sit closer together. This is presentation-only CSS and does not change the core menu markup or behavior.

## v2.0.6 adjustment

The theme styles the core-owned pinned-post area and the core-owned three-dot post-options menu introduced in Bonumark Stream v0.5.13 and newer. The theme does not decide what is pinned, expose unpublished content, add post actions, or contain application logic.

## v2.0.5 adjustment

The theme now styles the core-owned scheduled-post composer introduced in Bonumark Stream v0.5.5 and newer. The schedule control remains compact until selected, then reveals an inline date/time panel with timezone and cancellation controls. No scheduling logic, JavaScript, routes, or publishing behavior is included in the theme.

## v2.0.4 adjustment

The header now gets a restrained orange edge and soft glow to match the cards visually while keeping the header calmer than the stream content.

## v2.0.3 adjustment

The theme tightened the header-to-feed spacing so logged-out views do not create a large empty gap above the first card.

## v2.0.2 adjustment

The theme keeps the stronger avatar treatment while reducing the orange card wash, border intensity, and glow so orange returns to being an accent instead of dominating every card.
