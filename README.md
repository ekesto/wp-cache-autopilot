# WP Cache Autopilot

WP Cache Autopilot is a cache lifecycle automation system for WordPress. It keeps cache fresh automatically by precisely invalidating affected pages and rebuilding them safely after content changes.

This repository contains the public changelogs for the included plugins:

• **Cache Invalidator** – decides what cache must refresh  
• **Cache Warmup** – rebuilds cache after changes

WP Cache Autopilot works alongside existing cache plugins and focuses on cache freshness, not cache storage.

## The problem

WordPress cache improves performance but creates a freshness risk. Content updates may not appear immediately, while full cache flushes cause cold pages and traffic spikes.

## The solution

WP Cache Autopilot automates the cache lifecycle:

1. Detect content changes  
2. Identify affected pages  
3. Purge cache precisely  
4. Warm affected URLs automatically  

Result:

- Less stale content
- Fewer full cache flushes
- Reduced regeneration spikes
- Less manual cache management

## Included plugins

### Cache Invalidator
Handles cache invalidation (automatic cache clearing):

- Group-based invalidation rules
- Relationship propagation
- Archive inclusion
- Multilingual awareness
- Timed invalidation rules
- Developer hooks and filters

### Cache Warmup
Handles cache warmup (cache preload):

- Targeted warmup after invalidation
- Full sitemap warmup
- Queue processing via WP-Cron
- Priority handling for important URLs

## Integrations

WP Cache Autopilot integrates with supported WordPress cache plugins via cache adapters. It does not replace cache plugins — it keeps them accurate.

## Changelogs

This repository publishes release changelogs for:

- Cache Invalidator
- Cache Warmup

For installation, configuration, and usage documentation, see the official documentation.

## Links

Website:  
[https://wpcacheautopilot.com](https://wpcacheautopilot.com)

Documentation:  
[https://wpcacheautopilot.com/docs](https://wpcacheautopilot.com/docs)

Getting Started:  
[https://wpcacheautopilot.com/docs/getting-started/](https://wpcacheautopilot.com/docs/getting-started/)

Support:  
[https://wpcacheautopilot.com/support/](https://wpcacheautopilot.com/support/)

## About

WP Cache Autopilot is developed and maintained by Beat Schenkel (ekesto), an independent Swiss WordPress developer focused on solving real cache freshness problems for production WordPress sites.
