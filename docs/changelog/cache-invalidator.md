<!-- AUTO-GENERATED FROM README. DO NOT EDIT -->
# Cache Invalidator Changelog

== Changelog ==

= 7.3.19 = 2026-03-29
* Fix: Improved Freemius deployment workflow.
* Fix: Moved uninstall cleanup to a lifecycle uninstall hook for Freemius compatibility.

= 7.3.18 = 2026-03-29
* Fix: Improved Freemius deployment workflow.

= 7.3.17 = 2026-03-29
* Fix: Improved Freemius deployment workflow.

= 7.3.16 = 2026-03-29
* Fix: Improved Freemius deployment workflow.

= 7.3.15 = 2026-03-29
* Fix: Improved Freemius deployment workflow.

= 7.3.14 = 2026-03-29
* Fix: Release publishing now uses GitHub CLI (`gh release create/upload`) instead of the Node 20-based `softprops/action-gh-release` action.
* Fix: Removed remaining Node 20 deprecation warnings from the release pipeline while preserving deterministic `-dist.zip` upload behavior.

= 7.3.13 = 2026-03-29
* Enhancement: Release workflow now syncs changelog docs to the public repo as a dependent job after successful tag builds.
* Fix: Updated sync workflows to `actions/checkout@v5` to align with GitHub Actions Node.js 24 migration requirements.
* Fix: Added `.gitmodules` to `.distignore` so VCS submodule metadata is excluded from distribution archives.

= 7.3.12 = 2026-03-29
* Fix: Corrected release CI version extraction escaping so plugin header parsing no longer returns an empty value in GitHub Actions.
* Fix: Restored reliable tag/version validation by parsing `* Version: x.y.z` header lines correctly during release builds.

= 7.3.11 = 2026-03-29
* Fix: Release CI now parses plugin header `Version:` values correctly from root PHP files, preventing false tag/version mismatch failures.
* Fix: Tag verification now compares against the extracted semantic version (for example `7.3.11`) instead of the literal `Version:` token.

= 7.3.10 = 2026-03-29
* Fix: Release CI now installs WP-CLI from the stable gh-pages PHAR URL, avoiding curl HTTP failures (`exit 22`) on tag builds.
* Fix: Pinned `wp-cli/dist-archive-command` to `v3.1.0`, which is compatible with runner WP-CLI `2.12.x`.

= 7.3.9 = 2026-03-29
* Fix: Release CI now installs a deterministic WP-CLI `2.13.0` PHAR before `wp-cli/dist-archive-command` installation, preventing the WP-CLI dependency mismatch (`^2.13`).
* Fix: Added an explicit WP-CLI version guard in release CI so incompatible runner versions fail early with a clear error.

= 7.3.8 = 2026-03-29
* Fix: Release CI now force-updates WP-CLI before installing `wp-cli/dist-archive-command`, resolving the `wp-cli/wp-cli ^2.13` dependency error.
* Enhancement: Updated checkout action to `actions/checkout@v5` to align with GitHub Actions Node.js 24 migration warnings.

= 7.3.7 = 2026-03-29
* Fix: Added explicit GitHub Actions `contents: write` permission so release creation succeeds on tag-triggered runs.
* Fix: Keeps automated distribution publishing on Releases functional for the `-dist.zip` artifact.

= 7.3.6 = 2026-03-29
* Fix: Restored `dist/` exclusion in `.distignore` to keep local/CI packaging artifacts out of release ZIPs.
* Fix: Release ZIP hygiene validation now allows required runtime `build/` assets while still blocking development-only paths.

= 7.3.5 = 2026-03-29
* Fix: Release CI now installs the WP-CLI `dist-archive` package before building distribution archives.
* Enhancement: Release packaging now fails fast when `.distignore` is missing and publishes a single deterministic `-dist.zip` asset.
* Fix: Added release ZIP hygiene validation to fail builds if development files are detected in the distribution artifact.

= 7.3.4 = 2026-03-28
* Enhancement: Refined admin settings SCSS to use shared semantic color tokens for more consistent panel, modal, table, and plugin-meta styling.
* Enhancement: Reworked public docs structure, cross-links, and scenario guidance for clearer invalidation and warmup documentation.
* New: Added legal-page source documents for Terms of Service, Privacy Policy, and Imprint / Legal Notice under `legal/`.
* Enhancement: Added a GitHub workflow to sync the `readme.txt` changelog into the public documentation repo on `main` updates.
* Enhancement: Setup changelog workflow.

= 7.3.3 = 2026-03-25
* Enhancement: Added shared `wp_cache_autopilot_capability` capability filter support (default `manage_options`) across settings and protected REST actions.
* Enhancement: Refined settings labels/help text for clearer invalidation terminology across global, group, timed, and support-debug controls.
* Enhancement: Updated group and timed-rule action controls to compact icon actions, with settings panel z-index/panel spacing polish for improved admin UI usability.
* Enhancement: Refined public docs wording/section labels and requirements linking for terminology consistency.
* Enhancement: Forms invalidation now writes one compact `forms_change summary` debug line per event outcome with key counters and uncertainty flags.
* Fix: Moved forms manager boot and forms adapter hook-registration traces to verbose-only logging to reduce support debug noise.
* Enhancement: Added request-local dedupe for verbose debug traces to suppress exact duplicate lines.

= 7.3.2 = 2026-03-24
* Enhancement: Support debug View now opens an authenticated inline log URL so browser refresh always loads the latest log content.
* Fix: Added explicit REST root/nonce boot config for support debug View authentication stability in wp-admin.
* Fix: Removed false popup-warning notice from support debug View when browsers return a null window handle despite opening the tab.

= 7.3.1 = 2026-03-24
* Fix: Support debug mode now writes DEBUG entries to the shared support log when support mode is enabled.
* Enhancement: Support debug log filenames now default to `.txt` while keeping legacy `.log` filenames readable.
* Enhancement: Support debug panel now includes compact reload/view/delete icon actions, with View opening the current log file URL in a new tab.
* Fix: Updated cache invalidator docs wording/anchors for support-debug behavior and terminology consistency.

= 7.3.0 = 2026-03-23
* New: Added group target mode `Purge all cache` (`full_flush`) for post/CPT-triggered invalidation.
* Enhancement: Post/CPT triggers now run adapter `purgeAll()` and emit broad URL coverage when any matched enabled group uses `full_flush`.
* Fix: Relationship propagation controls are now disabled with a warning when group target mode is `Purge all cache`, while saved propagation values remain preserved.
* Enhancement: Standardized public extension hook names under the compact `ekesto_ci_*` namespace.
* Fix: Renamed invalidation emission action to `ekesto_ci_invalidation_urls` and updated all plugin docs/examples accordingly.

= 7.2.1 = 2026-03-19
* Fix: Forms invalidation now resolves Contact Form 7 hash-based identifiers and legacy numeric IDs as equivalent references for match, purge, and emission flows.
* Fix: Ninja Forms invalidation now listens to both legacy `nf_*` and current `ninja_forms_*` admin form lifecycle hooks, with request-local dedupe to prevent duplicate dispatch.
* Fix: Selected-pages target IDs are now normalized and deduplicated in the settings UI, preventing mixed-type duplicate IDs (for example `123` and `"123"`).
* Fix: In selected-pages mode, saving with a complete selector list now removes stale/deleted target page IDs so ghost selections no longer inflate summary counts.
* Fix: Selected-pages summary now shows a warning notice when saved IDs cannot be previewed from the loaded selector dataset (deleted targets or truncated list).
* Fix: `Select pages` modal height is now locked per open session to prevent search/filter layout jumps, and the lock is released on window resize to restore responsive sizing.

= 7.2.0 = 2026-03-18
* New: Added built-in WooCommerce relationship defaults for variation parents, linked products (`_upsell_ids`, `_crosssell_ids`, `_children`), and option-backed core pages (shop, cart, checkout, my account, terms).
* Enhancement: Added internal `RelationshipDefaultsProvider` and kept default assembly order stable (ACF defaults, Woo defaults, filter extensions).
* Enhancement: Added definition-level dedupe so overlapping built-in and custom relationship definitions do not execute duplicate lookups.
* Enhancement: Kept `ekesto_ci_relationship_meta_keys` as the extension/override layer after built-in defaults.
* Fix: Updated relationship and WooCommerce docs wording to describe baseline Woo propagation as built-in behavior.

= 7.1.2 = 2026-03-17
* Enhancement: Added fuzzy search for page target selection in the settings modal (title and URL slug matching).
* Enhancement: Added inline highlight rendering for matched title and URL slug fragments in selector rows.
* Fix: Kept select-all, row toggle, and filtered-selection behavior unchanged while search metadata is propagated through the table.
* Enhancement: Clarified `ekesto_ci_widget_targets` docs to describe post-ID targeting and added a custom-post-type (`book`) mapping example.
* Fix: Removed legacy relationship-definition compatibility (`meta_key`/`multiple`) from runtime normalization and docs; strategy-based `kind` definitions are now required.
* New: Added project-level multilingual fanout policy toggles in Global Invalidation settings: `multilingual_fanout_post_triggers_enabled` and `multilingual_fanout_non_post_triggers_enabled`.
* Enhancement: Unified multilingual fanout execution across post, async, taxonomy, presentation, forms, comments, metadata, timed invalidation, and full-flush emitted URL paths.
* New: Added `ekesto_ci_multilingual_fanout_mode` filter to override computed fanout mode per trigger context.
* Enhancement: Extended multilingual context reporting with `fanout_mode` and `fanout_languages` in purge/emission metadata for downstream observability.
* Fix: Corrected async multilingual fanout isolation per queued job and added Polylang URL-model fanout mapping for URL-target expansion.

= 7.1.1 = 2026-03-15
* New: Added v1 documentation landing/overview content with cross-linked docs entry points and deep section links.
* Enhancement: Clarified invalidation terminology in settings/help text (e.g. `Async deep invalidation`, timed invalidation target modes).
* Enhancement: Refined plugin readme wording around cache invalidation decision-engine responsibilities and best-effort cache purge behavior.

= 7.1.0 = 2026-03-13
* New: Added `ekesto_ci_post_target_mappings` support for non-public trigger post types without scope/group membership (mapped target IDs purge directly).
* Enhancement: Added a practical, fully commented `ekesto_ci_post_target_mappings` usage example and consolidated filter docs into one canonical section.
* Fix: Preserved GUI/group-managed behavior for public trigger post types with no matched scope/group (no mapping-only bypass).

= 7.0.1 = 2026-03-12
* Fix: Prevented WP Super Cache full-cache purge fatals on single-site installs by avoiding multisite-only purge arguments when `get_blog_option()` is unavailable.
* Fix: Preserved WP Super Cache multisite purge behavior by continuing to pass the current blog ID when multisite blog APIs are loaded.

= 7.0.0 = 2026-03-12
* New: Added first-party multilingual resolvers for WPML, Polylang, and TranslatePress.
* Enhancement: Introduced deterministic multilingual resolver detection order (WPML -> Polylang -> TranslatePress) with `ekesto_ci_language_resolver` remaining the final override.
* Enhancement: Target-page invalidation from post/CPT triggers now applies resolver-model language fanout for object-model and URL-model integrations.
* Enhancement: Emitted multilingual context now reports resolver-aware metadata (`resolver`, `resolver_model`, `languages`) instead of hardcoded WPML values.
* Fix: Added migration-safe backward-compatible WPML resolver handover class while moving built-ins under `Multilingual/Resolvers`.
* Fix: Generalized multilingual resolver contracts for dual translation models (object and URL), which requires custom resolver implementations to update for this release.

= 6.1.0 = 2026-03-12
* New: Added cache adapters for WP Rocket, W3 Total Cache, and FlyingPress.
* Enhancement: Added URL-level purge support for the new adapters via their native APIs/actions.
* Enhancement: Extended adapter manager fallback chain to include the new adapters after existing priority entries.

= 6.0.0 = 2026-03-10
* New: Strategy-based relationship definitions in `ekesto_ci_relationship_meta_keys` (`meta_exact`, `meta_serialized`, `post_parent`, `option_id`, `callback`).
* Enhancement: Native ACF auto-discovery now feeds the same normalized relationship-definition pipeline used by custom integrations.
* Enhancement: Relationship resolver now supports serialized integer matching and framework-agnostic documentation examples for WooCommerce, Meta Box, and The Events Calendar.

= 5.0.4 = 2026-03-09
* Enhancement: Unified plugin lifecycle flow under `Lifecycle` with explicit activation, deactivation, and guarded upgrade reconciliation.
* Fix: Moved timed-sync version state handling out of runtime bootstrap and into lifecycle upgrade handling for safer updates.
* Fix: Text domain loading now runs at `init` priority `0` to reduce early translation-load notice risk.
* Fix: Uninstall cleanup now removes lifecycle lock/sync state options and transient.

= 5.0.3 = 2026-03-06
* Fix: Bootstrap now preflights boot-critical classes and fails closed on incomplete plugin packages.
* Fix: Timed schedule reconciliation now defers heavy sync work away from sensitive update requests.
* Enhancement: Added local release verification for runtime files, build artifacts, metadata versions, and optional zip contents.

= 5.0.2 = 2026-03-05
* Fix: Standardized settings modal CSS class namespace across modal markup and styles.
* Enhancement: Synced built settings assets with modal class-name updates.

= 5.0.1 = 2026-03-05
* Fix: Removed `all`-hook based full-flush trigger interception that could cause excessive hook recursion and memory exhaustion.
* Fix: Restored direct extension full-flush hook registration flow for stable runtime behavior.

= 5.0.0 = 2026-03-05
* New: Added centralized invalidation emission helper with `ekesto_ci_additional_urls`, comment invalidation listener, and meta-change invalidation listener.
* New: Added extensibility filters for language resolver, runtime full-flush triggers, option-change trigger mapping, and post-type meta-change mapping.
* Enhancement: Added new global toggles for comment changes and theme switch changes in settings.
* Fix: Full-flush extension trigger map is now evaluated at runtime so late-registered filters are honored.
* Fix: `ekesto_ci_additional_urls` now uses the canonical callback contract `(array $urls, array $context): array`.

= 4.4.0 = 2026-03-04
* New: Page target mode support (`Selected pages` / `All pages`) for group settings and timed invalidation rules
* Enhancement: Modal-first page target selection UX with compact selected-page summaries (count + preview rows)
* Enhancement: Group create/edit now uses native WordPress modal flow
* Fix: Unified modal layout classes across settings modals to prevent footer/background inconsistencies

= 4.3.0 = 2026-03-04
* New: Timed invalidation rules in Settings tab with daily time + selected page ID targets (site timezone)
* New: Cron-backed timed invalidation scheduler with per-rule scheduling, cleanup, and emitted timed trigger context
* Enhancement: Settings REST payload now includes `timed_invalidation` and `site_timezone`
* Enhancement: Scheduled publish transitions (`future` -> `publish`) now emit a distinct `scheduled_publish` reason key

= 4.2.0 = 2026-03-02
* New: Forms invalidation module with adapter coverage for Contact Form 7, WPForms, Gravity Forms, and Ninja Forms
* New: Builder-aware reference scanning with centralized builder adapters and confidence-based scan profiles
* Enhancement: Global settings now include `forms_enabled` and `forms_global_fallback_enabled` toggles
* Enhancement: Cache adapter architecture moved to `src/Caching` with concrete adapters under `src/Caching/Adapters`
* Fix: Forms fallback path now limits broad invalidation to configured post/page cache targets only

= 4.1.3 = 2026-03-01
* Fix: Refreshed packaged admin build assets for the settings UI
* Enhancement: Normalized build artifact set in plugin distribution

= 4.1.2 = 2026-03-01
* Enhancement: Added explicit trigger metadata in emitted invalidation context (`trigger_class`, `trigger_event`)
* Enhancement: Async invalidation context now includes aggregated trigger details (`trigger_kinds`, `trigger_reasons`)

= 4.1.1 = 2026-03-01
* New: Global master switch to pause/resume all invalidation paths (post, taxonomy, presentation, and async)
* Enhancement: Clarified settings/admin wording for engine-wide pause behavior
* Fix: Global paused admin notice no longer appears on the plugin's own settings screen
* Fix: Async queue enqueuing/scheduling/processing now hard-stops when master switch is off

= 4.1.0 = 2026-03-01
* New: Presentation-layer invalidation triggers for menus, customizer saves, widget updates, reading settings, and permalink settings
* New: Block-entity coverage expanded with `wp_navigation` trigger handling
* New: Synced pattern invalidation with best-effort reference scan and global fallback
* New: Archive URL invalidation support for post type archives and publicly queryable taxonomy archives
* New: Adapter URL-purge capability path with emitted URL fallback when direct URL purge is unavailable
* New: Filter `ekesto_ci_widget_targets` for mapping widget changes to explicit post IDs
* New: Filter `ekesto_ci_archive_urls` for archive URL target customization
* New: Filter `ekesto_ci_presentation_trigger_enabled` for runtime trigger gating
* New: Filter `ekesto_ci_should_fallback_global` for synced-pattern fallback control

= 4.0.0 = 2026-02-28
* Enhancement: Simplified propagation model to one source of truth using `groups[*].propagation` in both simple and advanced modes (breaking change)
* Fix: Simple mode propagation toggles now persist independently per post type/group tab
* Enhancement: Settings-tab async controls now bulk-apply async propagation values across all groups
* Fix: Removed legacy `simple_propagation` handling from REST payloads and option sanitization

= 3.0.0 = 2026-02-28
* Breaking: Refactored `Settings` architecture to DI-based services and removed public static behavior methods from `Settings`
* New: `Settings` is now a constants-only compatibility boundary (option key, route/path slugs, handles, defaults, exclusions)
* New: Settings internals split into focused services (repository, sanitizer, payload builder, REST controller, admin page)
* New: PHP is now the single source of truth for settings app config (`config` + `initial` passed to JS boot object)
* Fix: `GroupResolver::getWatchedPostTypesForScope()` advanced-mode path no longer references undefined variable
* Internal: Runtime consumers now resolve settings through plugin-managed services instead of `Settings::*` static methods

= 2.0.1 = 2026-02-19
* Improved: UI
* Fix: Multilingual related issues in page list.
* New: Excluded post types (page, attachment) bypass scope/group system — editing these post types purges the post itself directly without requiring group configuration
* New: Centralized exclusion constant `Settings::EXCLUDED_POST_TYPES` for consistent post type filtering across codebase

= 2.0.0 = 2026-02-19
* New: Relationship propagation — when a related post (e.g. collaborator) changes, affected host posts (e.g. events) are automatically purged via ACF relationship field auto-discovery
* New: Taxonomy propagation — term edits, deletions, and reassignments trigger targeted invalidation of affected posts and group target pages, scoped to watched post types only
* New: Async deep invalidation — background processing via WP-Cron with configurable delay, deterministic deduplication keys, safe queue drain, and 200-item size cap
* New: Single-emission policy — async mode defers URL emission to the processor; sync mode emits at end of processing
* New: Request-level dedup — prevents double emission when `save_post` and `set_object_terms` fire for the same post in one request
* New: PropagationPanel UI per group tab with toggles for relationships, taxonomies, and background processing
* New: GroupResolver class for mode-aware scope resolution with `getWatchedPostTypes()` helper for taxonomy scoping
* New: Filter `ekesto_ci_relationship_meta_keys` for extending relationship field discovery
* New: `Settings::isAsyncAvailable()` enforces `DISABLE_WP_CRON` at runtime — async scheduling is hard-blocked when cron is disabled
* New: ACF relationship map transient is multisite-aware (keyed per blog_id)
* New: Async processor re-resolves host posts from trigger info for deterministic results
* Fix: Advanced mode group resolution — editing a member post type (e.g. collaborator in an "event" group) now correctly resolves and purges the group's target pages
* Fix: `DISABLE_WP_CRON` logic — corrected operator precedence bug that could schedule cron when it shouldn't

= 1.2.11 = 2026-02-18
* Improved: UX

= 1.2.10 = 2026-02-18
* Improved: UX

= 1.2.9 = 2026-02-17
* Fix: Only register LiteSpeed Cache REST no-cache filter when LSC is active — prevents fatal error when switching to another cache plugin
* Enhancement: Dedicated CSS class variants for group list and page selection tables
* Enhancement: Renamed _footer.scss to _adapter-info.scss with scoped .eci-adapter-info styles

= 1.2.8 = 2026-02-15
* Added: Search functionality with keyboard shortcut (Shift+F) to filter pages in group settings
* Added: Click-to-toggle page selection — click anywhere on a table row to select/deselect
* Added: Visual feedback for selected pages in the table
* Added: Indeterminate checkbox state when some (but not all) pages are selected
* Added: NextControls wrapper components for standardized WordPress UI controls
* Improved: Page selection table UI with better styling and visual hierarchy
* Improved: Overall settings page styling with new SCSS partials for search and text

= 1.2.7 = 2026-02-14
* Added: Settings link on plugin page

= 1.2.6 = 2026-02-14
* Fix: Make preventLscCaching method public for filter callback

= 1.2.5 = 2026-02-14
* Fix: Prevent LiteSpeed Cache from caching plugin REST API responses — uses rest_pre_dispatch filter for reliable cache suppression

= 1.2.4 = 2026-02-14
* Fix: Prevent LiteSpeed Cache from caching REST API responses

= 1.2.3 = 14.2.26
* Fixed: Options weren't saved correctly on production server

= 1.2.2 = 14.2.26
* Missing build folder added.

= 1.2.1 = 14.2.26
* UI improvements

= 1.2.0 = 14.2.26
* New feature: Simple/Advanced group management modes — toggle post type visibility or create custom groups with multiple post types
* New components: ModeToggle, SimpleModePanel, AdvancedModePanel, GroupEditor, GroupList, CustomSection, ValidationErrors, SettingsTab
* REST API now supports mode, simple_mode_visibility, and custom_groups parameters
* Server-side validation for custom groups (unique labels, exclusive post type assignment)
* UI improvements: reusable panel layout (CustomSection), group key immutability hint and visual deactivation in edit mode

= 1.1.0 = 13.2.26
* New feature: Settings page goes REACT!

= 1.0.4 = 6.2.26
* Treat Site Editor template, template part, and global styles updates as full-site invalidations (purges target pages across all enabled groups).

= 1.0.3 = 6.2.26
* Now only `publish` pages are shown
* Improved documentation

= 1.0.2 = 6.2.26
* Github repo added

= 1.0.1 = 5.2.26
* Improved documentation with real-world customization examples

= 1.0.0 = 5.2.26
* Initial release with unified cache invalidation and trigger abstraction
