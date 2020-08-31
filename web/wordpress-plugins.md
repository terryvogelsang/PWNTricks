# Wordpress Plugins 

> Plugins are packages of code that extend the core functionality of WordPress. WordPress plugins are made up of PHP code and can include other assets such as images, CSS, and JavaScript. 
> Most WordPress plugins are composed of many files, but a plugin really only needs one main file with a specifically formatted DocBlock in the header.
Source : [Wordpress Plugin Handbook](https://developer.wordpress.org/plugins/intro/what-is-a-plugin/)

 A valid Wordpress plugin only needs to have a file with the following DocBlock:

```php
/**
 * Plugin Name
 *
 * @package           PluginPackage
 * @author            Your Name
 * @copyright         2019 Your Name or Company Name
 * @license           GPL-2.0-or-later
 *
 * @wordpress-plugin
 * Plugin Name:       Plugin Name
 * Plugin URI:        https://example.com/plugin-name
 * Description:       Description of the plugin.
 * Version:           1.0.0
 * Requires at least: 5.2
 * Requires PHP:      7.2
 * Author:            Your Name
 * Author URI:        https://example.com
 * Text Domain:       plugin-slug
 * License:           GPL v2 or later
 * License URI:       http://www.gnu.org/licenses/gpl-2.0.txt
 */
```

## Hosting path

Every plugins are hosted in the `/wp-content/plugins/<plugin-name>`

## Hooks

The 3 basic hooks you’ll need when creating a plugin are the `register_activation_hook()`, `the register_deactivation_hook()`, and the `register_uninstall_hook()`.

The activation hook is run when you activate your plugin. You would use this to provide a function to set up your plugin — for example, creating some default settings in the options table.

The deactivation hook is run when you deactivate your plugin. You would use this to provide a function that clears any temporary data stored by your plugin.

These uninstall methods are used to clean up after your plugin is deleted using the WordPress Admin. You would use this to delete all data created by your plugin, such as any options that were added to the options table.


## Access control

The `is_admin()` conditional does not check if the user is an administrator; use `current_user_can()` for checking roles and capabilities.


## Available Functions
WordPress includes many other functions for determining paths and URLs to files or directories within plugins, themes, and WordPress itself. 

### Plugins

`plugins_url()`
`plugin_dir_url()`
`plugin_dir_path()`
`plugin_basename()`

### Themes

`get_template_directory_uri()`
`get_stylesheet_directory_uri()`
`get_stylesheet_uri()`
`get_theme_root_uri()`
`get_theme_root()`
`get_theme_roots()`
`get_stylesheet_directory()`
`get_template_directory()`

### Site Home

`home_url()`
`get_home_path()`

### WordPress

`admin_url()`
`site_url()`
`content_url()`
`includes_url()`
`wp_upload_dir()`

### Multisite

`get_admin_url()`
`get_home_url()`
`get_site_url()`
`network_admin_url()`
`network_site_url()`
`network_home_url()`
