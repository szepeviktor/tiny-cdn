=== Tiny CDN ===
Contributors: szepe.viktor
Donate link: https://szepe.net/wp-donate/
Tags: CDN, content delivery network, optimization, performance
Requires at least: 4.0
Tested up to: 4.9
Stable tag: 0.2.0
License: GPLv2

Use an origin pull CDN with very few lines of code.

== Description ==

Use an origin pull CDN with very few lines of code.

* Works with custom /wp-content location
* Does not support multisite installations

Pull requests are welcome on [GitHub](https://github.com/szepeviktor/tiny-cdn).

This plugins has no user interface.

Set /wp-includes (optional) and /wp-content (optional) CDN URL-s in your wp-config.php.

    // No trailing slash!
    define( 'TINY_CDN_INCLUDES_URL', 'https://d2aaaaaaaaaaae.cloudfront.net/wp-includes' );
    define( 'TINY_CDN_CONTENT_URL', 'https://d2aaaaaaaaaaae.cloudfront.net/wp-content' );

== Installation ==

This section describes how to install the plugin and get it working.

1. Upload `tiny-cdn.php` to the `/wp-content/plugins/` directory
1. Activate the plugin through the 'Plugins' menu in WordPress

== Frequently Asked Questions ==

= How to configure? =

Hook into these filters before `template_redirect` time.

    // Disable rewriting
    add_filter( 'tiny_cdn_disable', '__return_true' );

    // Don't rewrite for these users
    add_filter( 'tiny_cdn_capability', function () { return 'edit_pages'; } );

    // This is a regular expression to exclude single files
    add_filter( 'tiny_cdn_excludes', function () { return '#\.php#'; } );

== Changelog ==

= 0.2.0 =
* Fix hook timing for `wpseo_xml_sitemap_img_src` filter
* Introduce filters before the template runs

= 0.1.6 =
* Big typo in handling image thumbnails

= 0.1.5 =
* Add support for Yoast's `wpseo_xml_sitemap_img_src` filter

= 0.1.4 =
* Filter post thumbnail too

= 0.1.3 =
* First release on WP.org
