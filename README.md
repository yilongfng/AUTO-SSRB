# AUTO-SSRB

**Automatic Star Ratings for WordPress Posts**

AUTO-SSRB is a practical WordPress integration workflow that connects [Simple Star Rating Block](https://wordpress.org/plugins/simple-star-rating-block/), post custom fields, and a shared post template to automate star-rating display.

Instead of manually inserting and configuring a rating block in every post, authors enter a rating in the post's custom field. The shared template then displays the corresponding stars automatically.

## Why AUTO-SSRB?

WordPress sites often have useful plugins, custom fields, and template systems, but these components do not always work together automatically.

AUTO-SSRB demonstrates how to connect these existing capabilities without building a separate rating engine or replacing the upstream plugin.

The workflow aims to:

- Reduce repetitive manual work for authors.
- Keep rating data associated with individual posts.
- Display ratings consistently through a shared template.
- Reuse existing WordPress functionality.

## How It Works

The reference workflow consists of four steps:

1. A rating value is stored in a WordPress post custom field.
2. Simple Star Rating Block (SSRB) reads the custom-field value.
3. The rating block is configured in a shared single-post template.
4. The template displays the rating automatically for each applicable post.

The reference implementation uses:

| Component | Configuration |
|---|---|
| Upstream rating plugin | Simple Star Rating Block 0.3 |
| Rating custom-field key | `film_rating` |
| Custom-field reading option | `useCustomField=true` |
| Template integration | Shared single-post template |

## Verified Implementation

The core workflow has been implemented and tested on a self-hosted WordPress website.

Verified results include:

- The rating is retrieved from the post's `film_rating` custom field.
- The shared single-post template handles the rating display.
- Authors do not need to insert a rating block into every post body.
- Both **4.5** and **2.5** ratings display correctly, including half-stars.

These results describe one tested reference implementation. They do not establish universal compatibility with all WordPress themes, template systems, or content types.

## Intended Use

AUTO-SSRB is not limited to film-review websites.

The same integration approach may be useful for self-hosted WordPress blogs that associate ratings with posts, including reviews of products, books, services, and other subjects.

The currently verified scope focuses on:

- Standard WordPress posts.
- Ratings stored as post custom-field metadata.
- Automatic display through a shared single-post template.

Custom post types, special page templates, and other theme configurations remain areas for further testing.

## Project Principles

- **Integrate existing tools:** Build on useful WordPress plugins and features.
- **Automate repetitive tasks:** Avoid manual rating-block insertion in every post.
- **Keep the workflow practical:** Prefer clear, reproducible integration steps.
- **Be transparent:** Separate verified results from assumptions and untested possibilities.
- **Learn from the community:** Use real-world testing to guide improvements.

## Project Documentation

- [Project Status](docs/PROJECT_STATUS.md)
- [Integration Guide](docs/INTEGRATION_GUIDE.md)
- [Project Introduction (Chinese)](docs/PROJECT_INTRODUCTION_CN.md)
- [Community Feedback and Participation](docs/COMMUNITY_FEEDBACK.md)

## Community Participation

Feedback, reproduction reports, and suggestions are welcome from WordPress site owners, theme users, and developers.

Useful contributions include:

- Testing the workflow in other WordPress environments.
- Exploring different themes and template systems.
- Reporting issues with custom-field retrieval or rating display.
- Suggesting improvements to the documentation and integration approach.

Please distinguish individual testing results from generally verified compatibility.

GitHub Issue templates are available for:

- Feature requests and improvement suggestions.
- Bug reports and reproduction details.

## Repository Scope

This project shares the integration workflow, its documentation, and reviewed reusable supporting code where appropriate.

The reference implementation is used to document and verify the workflow. Website-specific configuration, private site data, credentials, and unrelated backup materials are not part of the public project.

## License

Unless otherwise noted, AUTO-SSRB's original code and documentation are licensed under the GNU General Public License v2.0 or later (GPL-2.0-or-later). See the [LICENSE](LICENSE) file.

Simple Star Rating Block is a separate third-party project. It is not distributed in this repository, and its copyright and licensing remain with its respective authors.

## Acknowledgements

The reference implementation uses [Simple Star Rating Block](https://wordpress.org/plugins/simple-star-rating-block/).

AUTO-SSRB is an independent integration workflow. It does not claim authorship of, or affiliation with, the upstream plugin.
