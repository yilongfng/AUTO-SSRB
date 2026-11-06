# AUTO-SSRB — Project Status

**Last updated:** 2026-11-06

## 1. Project Overview

AUTO-SSRB is a WordPress integration workflow for automating star-rating display.

It connects an existing rating plugin, WordPress post custom fields, and a shared single-post template.

The workflow has been implemented and verified on one self-hosted WordPress website. This document records the verified implementation, current scope, and remaining work.

## 2. Reference Implementation

The tested reference implementation uses the following configuration:

| Item | Configuration |
|---|---|
| WordPress environment | Self-hosted WordPress |
| Upstream rating plugin | Simple Star Rating Block 0.3 |
| Rating custom-field key | `film_rating` |
| Template integration | Shared single-post template |
| Custom-field reading option | `useCustomField=true` |

## 3. Implemented and Verified

The following functionality has been implemented and tested:

- [x] A custom rating field is available for WordPress posts.
- [x] The rating value is stored in the `film_rating` custom field.
- [x] Simple Star Rating Block 0.3 reads the custom-field value.
- [x] The plugin's `useCustomField` option is enabled.
- [x] The rating block is configured in a shared single-post template.
- [x] Ratings are displayed without manually inserting a rating block into every post body.
- [x] Half-star values of **4.5** and **2.5** have both been tested and display correctly.

These results confirm the workflow in one tested WordPress environment. They do not establish universal compatibility.

## 4. Current Project Materials

The project currently provides:

- Documentation explaining the integration architecture and workflow.
- Reproducible configuration guidance.
- A reviewed, reusable MU Plugin code example.
- Community feedback and compatibility reporting templates.
- A GPL-2.0-or-later license for original project code and documentation.

The repository does not include the upstream rating plugin or website-specific configuration.

## 5. Remaining Work

The following work remains open:

- [ ] Test the workflow with additional themes and template configurations.
- [ ] Investigate support for other post types and page arrangements.
- [ ] Gather feedback and reproduction reports from other WordPress environments.
- [ ] Document additional compatibility findings after verification.

## 6. Current Scope and Limitations

The currently verified workflow focuses on:

- Self-hosted WordPress installations.
- Standard WordPress posts.
- Ratings stored as post custom-field metadata.
- Automatic display through a shared single-post template.
- Simple Star Rating Block 0.3 configured to read the custom-field value.

The following areas have not yet been sufficiently tested to claim general support:

- Custom post types.
- Special landing pages.
- Other theme and template systems.
- Different custom-field configurations.
- Other versions of the upstream rating plugin.

Compatibility should be confirmed through testing before being documented as supported.

## 7. Next Steps

The next phase focuses on community validation and broader compatibility testing:

1. Publish the project repository after the final content review.
2. Invite feedback and reproducible test reports from other WordPress users.
3. Test the workflow with additional themes and template configurations.
4. Investigate custom post type support and other possible use cases.
5. Update the documented compatibility boundaries based on verified results.

## 8. Project Transparency

AUTO-SSRB is a documented WordPress integration workflow, not a standalone plugin.

The project distinguishes between:

- Functionality already implemented and tested.
- Compatibility that has not yet been independently verified.
- Proposed improvements and possible future use cases.

A successful test in one environment does not establish compatibility with every WordPress installation, theme, template system, or content type.
