# Microblog Stream Theme

Version: 2.1.4  
Compatibility targets: Bonumark Stream 0.7.2 and 0.8.1  
Validation status: source/package checks passed; native Theme Health and visual acceptance pending.

Microblog Stream is a personal Bonumark Stream presentation theme. It preserves the compact orange-accent microblog identity while using Bonumark Stream Theme Architecture 2.0 to control safe composition on Profile, Stream Card, and Home.

## Important compatibility note

This v2.1.4 theme package sets its minimum core version to v0.7.2 and adds presentation for the federation surfaces supplied by v0.8.1. The earlier broad v0.5.120+ compatibility claim is narrowed to the supplied core baselines. Following and Conversation only become available when the core supplies those features. It builds on the v2.1.0 Declarative Layout Schema 1 migration. Profile, Stream Card, and Home use validated JSON composition. Site Header intentionally remains on the legacy core composition so the theme can preserve its Live microblog status chip and published-post count.

Older Microblog Stream theme packages that included PHP templates or JavaScript will not install on Bonumark Stream v0.4.x because themes are now code-free presentation packages.

## Structure

```text
microblog-stream-theme/
  theme.json
  README.md
  THEME-DATA.md
  layouts/
    profile.json
    stream-card.json
    home.json
  assets/
    css/theme.css
    images/screenshot.svg
```

## Theme boundary

Bonumark Stream core owns rendering, routing, permissions, publishing, comments, profiles, media, feeds, import/export, upgrades, and all application behavior.

This theme provides presentation only:

- metadata
- settings schema
- validated Layout Schema 1 JSON composition
- CSS
- images
- screenshot

It does not include PHP, JavaScript, HTML templates, routes, database logic, or helper files.

## Updating the design

Edit `layouts/*.json` to change the composition of the declared Profile, Stream Card, and Home surfaces. Edit `assets/css/theme.css` to change colors, typography, spacing, cards, header styling, media display, comments, profiles, and other visual presentation.

Do not add PHP, JavaScript, arbitrary HTML, templates, expressions, routes, or application logic. Bonumark Stream validates the declared layouts and continues to own all component markup and behavior.


## v2.1.4: ActivityPub Presentation Compatibility

This is a theme update for the planned jimlunsford.net upgrade from Bonumark Stream v0.7.2 to v0.8.1. It does not upgrade core or enable ActivityPub.

- Styles the core-owned Following timeline and Conversation view in the existing dark, orange-accented Microblog Stream design.
- Wraps long remote names and handles while preserving their full text.
- Gives Following actions a minimum 44-pixel height, visible keyboard focus, active Like/Boost states, and two-column mobile arrangement.
- Styles native content-warning disclosure controls, summaries, deleted-post notices, empty states, and delivery errors.
- Preserves complete single-image and gallery frames with `object-fit: contain`. Single images have a bounded height, galleries use two desktop columns and one narrow-screen column.
- Keeps the remote reply composer on the existing core Stream composer styling.
- Contains long federated comment handles, links, and code blocks on local posts.
- Preserves the three declarative layouts, screenshot, settings keys/defaults, supported capability declarations, and `microblog-stream` slug.
- Leaves the legacy core header in place, including the status chip, post count, and menu.

All pre-existing CSS rules are retained. New rules are scoped to Following/Conversation or comments containing the core federated-content wrapper. Core retains routing, sanitization, visibility, permissions, actions, media links, and form submission.

## Validation and remaining acceptance

Completed locally against the supplied v0.7.2 and v0.8.1 source packages:

- JSON and declared-file checks, package file allowlist, and preserved slug/settings/layout checks.
- Layout components, counts, nesting, and document structure checked against both supplied core registries.
- CSS token/declaration parsing, selector parsing, and new-rule scope checks. Existing browser-specific details-marker and file-button selectors are retained and excluded from the generic selector compiler.
- Static selector/cascade checks on representative Following and Conversation markup at 360, 390, 680, and 1280 pixels: action minimum height and automatic height, remote-name wrapping, and full-frame image fitting.

These are source and static cascade checks, not browser layout measurements. The cloud browser rejected the local fixture URL under its security policy. PHP was unavailable locally, so the native installer and Theme Health were not executed. No production site, staging site, database, or remote account was changed. Live federation delivery was not tested.

Before production use, complete the following on a staging installation running the exact v0.8.1 package:

1. Back up both existing Microblog Stream theme directories and record the selected theme/settings. Install v2.1.4 and run native Theme Health; confirm its slug is `microblog-stream` and version is `2.1.4`.
2. At desktop width, 390 × 844, and 360 × 800, inspect populated Following and Conversation. Confirm no page overflow or clipped content, usable full remote handles, legible controls, keyboard focus, and readable deleted/empty/error states.
3. Open and close content warnings with pointer and keyboard. Confirm concealed content remains concealed until opened and interaction does not trigger unintended card navigation.
4. Inspect portrait/landscape single images and two-to-four-image galleries. Confirm full frames, correct ordering, usable media links, and normal opening behavior. Check video/audio controls when examples are available.
5. Use dedicated staging test accounts to verify Conversation, Back to Following, Reply, Like/Unlike, and Boost/Unboost. Confirm the native reply composer is usable and submits through core correctly.
6. Check Home, pinned posts, a local single post, existing/federated comments, Profile, navigation, search, archives, ordinary pages, media, and the logged-in composer. Verify the established design and header settings remain intact. Review the owner-only remote-reaction section when populated.
7. If installing the theme before the core upgrade, run native Theme Health and the ordinary public-page checks on v0.7.2 first. Federation surfaces will not exist there.

## Installation and rollback

This ZIP preserves the prior single-folder theme format. The Admin theme uploader recognizes it and splits private metadata/layouts from declared public assets. Use the theme uploader, not the core software upgrader. If this slug already exists, use the uploader's theme-update option.

If theme ZIP installation is unavailable on an intentionally locked installation, deploy with the existing site owner workflow. Do not change server permissions simply to install this theme. The mapping is:

| ZIP content under `microblog-stream-theme/` | Site destination |
| --- | --- |
| `theme.json`, `README.md`, `THEME-DATA.md`, `layouts/` | `_bonumark_stream/themes/microblog-stream/` |
| `assets/css/theme.css` | `assets/themes/microblog-stream/assets/css/theme.css` |
| `assets/images/screenshot.svg` | `assets/themes/microblog-stream/assets/images/screenshot.svg` |

Do not blindly unzip this single-folder package over the website root. Update both theme locations together, preserve the site's ownership model, and run Theme Health before activation. Only declared public assets belong in the public directory.

For a theme-only rollback, restore both backed-up theme directories together and retain the existing theme slug/settings. This does not roll back Bonumark core or its database migrations. A core upgrade has its own backup and recovery workflow.

## v2.1.3

Mobile Action Row Micro-Pass:

- keeps feed-card actions unchanged
- changes only narrow single-post action controls to an intentional two-column layout when Likes, Comments, Back to stream, and Post options are present
- places Likes and Comments on the first row, with Back to stream and Post options on the second row
- lets Back to stream span the row when no Post options menu is available
- preserves the normalized compact control heights, comment-form treatment, Profile composition, Stream Card composition, Home composition, and all core-owned behavior from v2.1.2

No declarative layout JSON changed in this pass. This is the final targeted responsive-control adjustment after the Density & Finish Pass.

## v2.1.2

Density & Finish Pass:

- tightens the Profile cover-to-identity overlap and reduces excess spacing inside the mobile identity hero without changing component order or ownership
- trims Profile rail and Featured spacing so the mobile Profile keeps its hierarchy without feeling padded section by section
- tightens Stream Card body rhythm and the spacing between header, content, previews, media, dividers, and actions on narrow screens
- normalizes Likes, Comments, Back to stream, and the Post options control to a common compact control height and visual weight
- slightly reduces compact mobile link-preview dimensions while preserving the readable thumbnail-and-copy treatment introduced in v2.1.1
- refines the mobile comment form density while keeping the full-width primary Post Comment action
- verifies that Profile photo placeholders seen in full-page mobile captures are not created by theme hiding/opacity rules; Bonumark Stream core intentionally lazy-loads Profile gallery images with low fetch priority, so this pass preserves that performance behavior

No declarative layout structure changed in this pass. Profile, Stream Card, and Home keep the v2.1.1 composition, and Site Header remains on the legacy core composition.


## v2.1.1

Visual Hierarchy & Responsive Composition Pass:

- binds the core-owned Profile cover and identity components into one declarative `microblog-profile-intro` group so the identity panel can overlap the cover edge without putting text on photography
- keeps About as the primary Profile story while consolidating Now, Interests, Links, and optional Details into one visually unified supporting rail
- gives Featured and Photos stronger destination-level hierarchy while keeping orange as an accent rather than a surface color
- preserves the established Stream Card identity on desktop but changes the narrow-screen composition so the avatar anchors the header row and the post body, previews, media, and actions recover the full card width
- replaces oversized stacked mobile link-preview images with compact thumbnail-and-copy cards while keeping the existing horizontal desktop preview
- tightens mobile Profile spacing and preserves a predictable single-column reading order
- leaves Site Header on the legacy core composition so Live microblog and published-post count settings remain available

All Profile data, media delivery, link-preview data, stream behavior, comments, actions, accessibility behavior, and application logic remain in Bonumark Stream core.


## v2.1.0

Migrates Microblog Stream onto Bonumark Stream Theme Architecture 2.0 without throwing away the theme's established identity:

- adds validated Declarative Layout Schema 1 composition for Profile, Stream Card, and Home
- keeps Site Header on the legacy core composition so the Live microblog status chip and post-count chip remain available
- turns the Profile into a deliberate desktop composition with a strong identity hero, About as the primary story, a compact supporting rail for Now/Interests/Links/Details, and full-width Featured and Photos sections
- preserves a predictable single-column Profile on smaller screens
- makes the classic avatar-left/content-right Stream Card structure explicit through declarative composition instead of depending on the legacy fixed wrapper
- separates Home into publish and timeline zones while leaving the composer, pinned-post behavior, feed rendering, and pagination in core
- reduces repetitive orange wash on every post card while keeping orange strong on identity, links, active controls, and avatar edges
- improves single-post reading rhythm and fully styles the core-owned comment form, including the Post Comment button and focus state
- targets Bonumark Stream v0.5.120 so the theme is aligned with the current declarative layout and Profile media contracts

No PHP, JavaScript, arbitrary HTML, SQL, routes, expressions, or application behavior were added to the theme.


## v2.0.12

Polishes the custom theme's Profile editor presentation for Bonumark Stream v0.5.87:

- enlarges editor labels, helper text, fields, and control hit areas so the expanded Profile form is easier to read and use
- improves spacing and internal rhythm across Identity, Featured Work, Photos, Links, Profile Settings, and Profile Portability
- gives Save Profile and Download Profile ZIP clear theme-consistent button styling
- strengthens Featured Work and Photos editor rows so they read as editable sections rather than cramped utility panels
- improves upload-control presentation, textarea padding, and mobile editor behavior without changing any core Profile behavior

All Profile storage, uploads, metadata, privacy, portability, permissions, and routing remain in Bonumark Stream core.

## v2.0.11

Updates the custom theme for the Profile system completed through Bonumark Stream v0.5.87:

- styles the current Profile identity hierarchy, including cover image, identity hero, headline, location, About, Now, Interests, Links, and optional Details
- styles the Profile editor sections for identity media, flexible links, settings, and owner controls
- styles deliberate Featured work cards and the Featured work editor without adding content-selection behavior
- styles the core-owned one-to-four Profile Photos contract, captions, full-image viewer links, photo editor previews, reordering controls, and responsive layouts
- styles the Profile portability section while leaving export generation and security in core
- removes the obsolete `profile_layouts` support declaration because Profile layouts are not a universal core capability
- top-aligns the public site shell so short pages, including an empty Stream, do not stretch into a large vertical gap
- preserves the theme's compact dark surfaces, circular avatar treatment, orange accent, and mobile behavior

All Profile storage, privacy, metadata, featured-item resolution, photo uploads, responsive image generation, viewer behavior, portability, routing, permissions, and Stream behavior remain in Bonumark Stream core.

## v2.0.10

Adds presentation support for the unified front-end publishing workflow completed in Bonumark Stream v0.5.49:

- styles the compact composer More options control and its Save draft, Continue in full editor, and Advanced options menu
- styles the Advanced metadata panel while keeping it hidden until deliberately opened
- styles the front-end Quick edit textarea, status area, Save button, and Cancel button
- expands the Post options menu cleanly for Quick edit, Open full editor, pinning, and recoverable trash
- gives Move to trash a restrained destructive treatment so it is not confused with normal editing actions
- preserves the compact composer layout on desktop and mobile
- declares support for the core-owned multi-photo gallery presentation already used by the theme

All draft saving, publishing, revisions, permissions, conflict detection, editing, trash recovery, and permanent deletion remain in Bonumark Stream core. The theme contains presentation-only CSS and metadata.

The theme still installs on Bonumark Stream v0.5.5 and newer. The unified composer, Quick edit, and recoverable front-end trash styling become active when the matching Bonumark Stream v0.5.49 markup is present.

## v2.0.9

Updates the front-page composer preview for Bonumark Stream v0.5.44 and newer:

- removes the legacy one-file flex layout that overrode the core multi-photo preview grid
- displays two to four selected photos in the core two-column preview layout
- lets preview thumbnails fill their cards without fixed 64-pixel sizing
- preserves the theme's dark surfaces, orange focus treatment, rounded controls, and remove-button warning state
- keeps upload handling, photo ordering, validation, publishing, and preview behavior in Bonumark Stream core

The theme remains compatible with Bonumark Stream v0.5.5 and newer. Multi-photo preview styling becomes active when the newer core gallery markup is present.

## v2.0.8

Adds presentation support for Local Places in Bonumark Stream v0.5.36 and newer:

- matches the Local Places composer panel to the existing scheduled-post panel
- styles the saved-place picker, nearby search, selected-place state, and add-place dialog
- styles public check-in location details inside stream cards
- keeps orange as an accent for active controls and hover states instead of tinting the entire panel
- contains presentation-only CSS, with all location permissions, storage, matching, and publishing behavior remaining in core

The theme still installs on Bonumark Stream v0.5.5 and newer. Local Places styling becomes active only when the core Local Places feature is present.

## v2.0.7

Tightens the vertical rhythm of the core-owned Post options dropdown:

- reduces excess space between Edit and Pin to Stream / Unpin from Stream
- keeps the two actions left-aligned and easy to tap
- contains presentation-only CSS, with no core behavior changes

## v2.0.6

Adds presentation support for the core-owned pinned-post and post-options work in Bonumark Stream v0.5.13 and newer:

- styles the Pinned area above the normal stream without adding pinning logic
- styles the three-dot Post options control and its Edit and Pin to Stream / Unpin from Stream actions
- lets the dropdown escape the post card cleanly and layer above the next card
- keeps the menu actions left-aligned and usable on mobile

The theme does not include PHP, JavaScript, database logic, routes, permissions, pin queries, or public visibility rules.

## v2.0.5

Adds presentation support for the scheduled-post front-end composer in Bonumark Stream v0.5.5 and newer:

- compact media and schedule toolbar controls
- inline schedule date/time panel
- active scheduling state for the submit button
- timezone and cancel-schedule presentation
- mobile schedule-panel layout
- hidden accessibility-only composer help text, matching the current core composer model

## v2.0.4

Adds a subtle matching orange header glow so the header feels connected to the post cards without turning the full header into a heavy accent block.

## v2.0.3

Tightened the header-to-feed spacing so logged-out views do not leave a large empty gap between the header and the first card.

## v2.0.2

Kept the stronger avatar treatment while reducing the orange card wash, border intensity, and glow so orange returns to being an accent instead of dominating every card.
