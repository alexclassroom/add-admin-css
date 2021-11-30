# Developer Documentation

This plugin provides [hooks](#hooks) for developer usage.

## Hooks

The plugin exposes a number of filters for hooking. Code using these filters should ideally be put into a mu-plugin or site-specific plugin (which is beyond the scope of this readme to explain).

### `c2c_add_admin_css` _(filter)_

The `c2c_add_admin_css` filter allows customization of CSS that should be added directly to the admin page head.

#### Arguments

* `$css` _(string)_ :
CSS styles.

#### Example

```php
/**
 * Add CSS to admin pages.
 *
 * @param string $css String to be added to admin pages.
 * @return string
 */
function my_admin_css( $css ) {
	$css .= "
		#site-heading a span { color:blue !important; }
		#favorite-actions { display:none; }
	";
	return $css;
}
add_filter( 'c2c_add_admin_css', 'my_admin_css' );
```

### `c2c_add_admin_css_files` _(filter)_

The `c2c_add_admin_css_files` filter allows programmatic modification of the list of CSS files to enqueue in the admin.

#### Arguments

* `$files` _(string)_ :
Array of CSS files.

#### Example

```php
/**
 * Add CSS file(s) to admin pages.
 *
 * @param array $files CSS files to be added to admin pages.
 * @return array
 */
function my_admin_css_files( $files ) {
	$files[] = 'http://yui.yahooapis.com/2.9.0/build/reset/reset-min.css';
	return $files;
}
add_filter( 'c2c_add_admin_css_files', 'my_admin_css_files' );
```
