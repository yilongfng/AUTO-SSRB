# AUTO-SSRB Integration Guide

This guide explains how to reproduce the reference AUTO-SSRB workflow on a self-hosted WordPress website.

The workflow connects Simple Star Rating Block, WordPress post custom fields, and a shared single-post template. It does not require a separate rating plugin or a custom rating interface.

## 1. Prerequisites

You will need:

- A self-hosted WordPress installation.
- A theme or template system that allows you to edit a shared single-post template.
- The Gutenberg block editor.
- Simple Star Rating Block 0.3.

Install and activate Simple Star Rating Block from the WordPress plugin directory.

## 2. Register the Rating Custom Field

The reference workflow uses the post custom-field key `film_rating`.

WordPress can register this field through a small Must-Use Plugin (MU Plugin). Create a PHP file in:

`wp-content/mu-plugins/`

For example, use the filename `auto-ssrb-rating-meta.php`.

If the `mu-plugins` directory does not exist, create it first.

Add the following code:

```php
<?php
/**
 * Plugin Name: AUTO-SSRB Rating Meta
 * Description: Registers a reusable rating field for standard WordPress posts.
 * SPDX-License-Identifier: GPL-2.0-or-later
 */

add_action('init', function () {
    register_post_meta('post', 'film_rating', [
        'type'          => 'number',
        'single'        => true,
        'show_in_rest'  => true,
        'auth_callback' => function ($allowed, $meta_key, $post_id) {
            return current_user_can('edit_post', $post_id);
        },
    ]);
});
```

WordPress automatically loads PHP files placed directly in the `mu-plugins` directory.

This code registers `film_rating` as a single numeric metadata value for standard posts and exposes it through the REST API. The permission callback checks whether the current user can edit the relevant post.

The example does not create a custom editing interface or implement rating display. Those responsibilities remain with WordPress and the upstream rating plugin.

## 3. Enable Custom Fields in Gutenberg

Open a post in the Gutenberg editor.

1. Open the three-dot menu (`...`) in the upper-right corner.
2. Select **Preferences**.
3. Enable **Custom Fields**.
4. Return to the editor.

The Custom Fields panel should now be available in the editor. Select `film_rating` from the custom-field dropdown. If it is not listed, save or reload the editor and check again.

Enter the rating value and save or update the post.

The reference workflow uses values within the 0–5 rating range. The registration code above does not implement range validation; it leaves rating behavior to the upstream plugin.

## 4. Add the Rating Block to a Shared Template

Open the theme's template editor and locate the shared **Single Post** template.

Add a Simple Star Rating Block to the template at the position where the rating should appear.

The block belongs in the shared template, not in every individual post body.

This allows the same template to display the rating associated with each post.

The exact template-editing interface depends on the active theme and its template system.

## 5. Enable Custom-Field Reading

Select the Simple Star Rating Block in the shared template.

Configure the block's custom-field reading option so that `useCustomField` is set to `true`.

The reference workflow uses the `film_rating` post custom field as the rating source.

Save the template.

## 6. Test the Integration

Create or update test posts with the following custom-field values:

- `4.5`
- `2.5`

Publish the posts and view them on the front end.

In the verified reference implementation:

- The rating block retrieves the value from the post's `film_rating` field.
- The shared Single Post template displays the rating automatically.
- Both 4.5 and 2.5 display correctly, including half-stars.
- No rating block needs to be inserted manually into each post body.

## 7. Scope and Compatibility

The reference implementation has been tested with:

- Simple Star Rating Block 0.3.
- Standard WordPress posts.
- The `film_rating` custom field.
- A shared Single Post template.
- The `useCustomField=true` setting.

This guide documents that tested workflow. It does not establish compatibility with every WordPress theme, template system, custom post type, or version of the upstream plugin.

Custom post types and other template configurations require separate testing.

## 8. Upstream Plugin

AUTO-SSRB is an integration workflow, not a replacement for Simple Star Rating Block.

The upstream plugin remains responsible for rendering the rating block and its rating behavior.

- [Simple Star Rating Block](https://wordpress.org/plugins/simple-star-rating-block/)
