# WP Cache Autopilot

WP Cache Autopilot is a cache lifecycle automation system for WordPress. It improves cache freshness by automatically determining which pages are affected by content changes, purging only those entries through supported cache plugins, and rebuilding them through controlled warmup execution.

This repository contains the public changelogs for the included plugins:

- **Cache Invalidator** – see [changelog](https://ekesto.github.io/wp-cache-autopilot/docs/changelog/cache-invalidator/)
- **Cache Warmup** – [changelog](https://ekesto.github.io/wp-cache-autopilot/docs/changelog/cache-warmup/)

Documentation lives on the product website. This repository exists only for release transparency and changelog history.

## Scope

WP Cache Autopilot does not replace cache plugins. Cache plugins handle storage and delivery. WP Cache Autopilot handles cache freshness automation.

Lifecycle handled:

1 Detect content changes  
2 Resolve affected URLs  
3 Purge via cache adapter  
4 Queue warmup requests  
5 Rebuild cache via paced execution  

## Included plugins

### Cache Invalidator

Determines which URLs must be refreshed after content changes.

Core capabilities:

- Group-based invalidation rules
- Relationship propagation
- Archive inclusion
- Multilingual awareness
- Timed invalidation rules
- Global invalidation controls
- Developer hooks and filters

### Cache Warmup

Rebuilds cache entries after invalidation.

Core capabilities:

- Targeted warmup after invalidation
- Full sitemap warmup
- Queue execution via WP-Cron
- Priority handling for important URLs
- Diagnostics and transport fallback logic

## Integrations

WP Cache Autopilot integrates with supported WordPress cache plugins through cache adapters. Behavior depends on adapter capabilities and hosting environment.

## Changelogs

This repository publishes changelogs for:

- Cache Invalidator
- Cache Warmup

For installation and configuration documentation:

https://wpcacheautopilot.com/docs

## Links

Website:  
[https://wpcacheautopilot.com](https://wpcacheautopilot.com)

Documentation:  
[https://wpcacheautopilot.com/docs](https://wpcacheautopilot.com/docs)

Getting Started:  
[https://wpcacheautopilot.com/docs/getting-started/](https://wpcacheautopilot.com/docs/getting-started/)

Support:  
[https://wpcacheautopilot.com/support/](https://wpcacheautopilot.com/support/)

## Maintainer

Developed and maintained by Beat Schenkel (ekesto), an independent Swiss WordPress developer.
