# Tiny CDN

Use an origin pull CDN with very few lines of code.

- Works with custom `/wp-content` location
- Does not support multisite installations @TODO wp-cdn-rewrite plugin `get_rewrite_path()`

### Installation

Set `/wp-includes` (optional) and `/wp-content` (optional) CDN URL-s in your `wp-config.php`.

```php
// No trailing slash!
define( 'TINY_CDN_INCLUDES_URL', 'https://d2aaaaaaaaaaae.cloudfront.net/wp-includes' );
define( 'TINY_CDN_CONTENT_URL', 'https://d2aaaaaaaaaaae.cloudfront.net/wp-content' );
```

### Configuration

Hook into these filters before `template_redirect` time.

```php
// Disable rewriting
add_filter( 'tiny_cdn_disable', '__return_true' );

// Don't rewrite for these users
add_filter( 'tiny_cdn_capability', function () { return 'edit_pages'; } );

// This is a regular expression to exclude single files
add_filter( 'tiny_cdn_excludes', function () { return '#\.php#'; } );
```

### Recommendations

- Aviod query strings on CDN, use [Resource Versioning](https://wordpress.org/plugins/resource-versioning/)
- Don't let browsers send cookies to CDN on a subdomain, set `define( 'COOKIE_DOMAIN', 'your.domain' );`
- Set canonical HTTP header for CDN requests `Link: <https://www.example.com/path/image.jpg>; rel="canonical"`
