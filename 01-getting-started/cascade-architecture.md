# Cascade Architecture: How a Page Is Built

## Overview

Cascade CMS separates **authored content** from the assets that define how that content is edited, rendered, and published. A page's fields, metadata, content type, configuration, template, blocks, and formats can all contribute to its output.

This is a conceptual guide, not a universal setup recipe: real Cascade implementations and permission models vary.

## Core asset types

| Asset | Main purpose |
| --- | --- |
| Site | Groups website content and related assets |
| Folder | Organizes content assets in a site |
| Page | Stores authored content and associated metadata |
| Data Definition | Defines structured fields available to authors |
| Metadata Set | Defines metadata fields associated with content |
| Content Type | Associates a Configuration Set, Data Definition, and Metadata Set |
| Template | Defines page structure and named regions |
| Configuration Set | Connects a Template, Outputs, and region assignments |
| Output | Represents a configured variant of rendered/published content |
| Block | Supplies shared or dynamic content for a region |
| Format | Converts structured/XML or API content into markup or other text, using Velocity or XSLT |
| Asset Factory | Helps create assets with preset choices and a base asset |

## Conceptual relationship

```text
Content Type
├── Data Definition ──> editable structured content
├── Metadata Set ─────> editable metadata
└── Configuration Set
    ├── Template ─────> HTML shell and named regions
    ├── Outputs ──────> output variants
    └── Regions ──────> Blocks and/or Formats

Page content + configuration + rendering
                    |
                    v
              Preview / publish
```

This diagram simplifies several relationships. For example, a Format assigned to a page's Default region can render its structured data; Blocks may be assigned to other regions and rendered using their own Formats.

## Example: an article page

Consider a **fictional** news site:

1. A developer defines **Heading**, **Summary**, and **Body** fields in a Data Definition.
2. A Content Type associates this definition with a Metadata Set and Configuration Set.
3. The Configuration Set selects a Template with regions such as **header**, **default**, and **footer**.
4. A Format renders the page's structured content as accessible article markup. Shared Blocks may provide the header and footer.
5. A content author creates a Page and enters the article content.
6. The page is previewed and, when approved, published using the site's configured output and publishing process.

These field and region names are examples only, not required Cascade conventions.

## Where common assets are managed

According to Hannon Hill's current documentation:

- **Content Types:** Manage Site → Content Types
- **Data Definitions:** Manage Site → Data Definitions
- **Metadata Sets:** Manage Site → Metadata Sets
- **Configuration Sets:** Manage Site → Configuration Sets
- **Formats:** Manage Site → Formats
- **Templates, Pages, and many Blocks:** site asset tree

Your installation's interface, version, and permissions determine what is available.

## Template vs. Format

A **Template** defines the page's broad structure, including named regions. A **Format** transforms content into rendered markup or text within the configured output. Cascade supports Velocity and XSLT Formats, but their syntax cannot be mixed in a single Format.

The distinction matters: a template can provide the article region while a Velocity Format converts Heading and Body fields into semantic HTML for that region.

## Inspection exercise

Use an existing page in an environment where you have permission to inspect settings.

1. Open a Page and identify its **Content Type**.
2. Find the Content Type's **Data Definition**, **Metadata Set**, and **Configuration Set**.
3. Inspect the Configuration Set's **Template**, **Outputs**, and region assignments.
4. Identify any **Blocks** or **Formats** assigned to regions.
5. Preview the Page. Connect each visible section to its content source or region.

**Verify:** You can explain where its editable fields come from, what defines its page shell, and what transforms its content into output.

This exercise requires no production modifications.

## Common confusion

- **Data Definition vs. Format:** fields for authors versus rendering logic.
- **Template vs. Format:** overall page shell versus content transformation.
- **Content Type vs. Configuration Set:** grouped authoring/configuration choices versus outputs and regions.
- **Preview vs. Publish:** viewing generated output versus publishing configured assets to a destination.
- **Product concept vs. local convention:** folder structures and shared-asset names vary between organizations.

## What to read next

Continue to [Cascade Development](../02-cascade-development/README.md) for configuration guides, then [Apache Velocity](../03-apache-velocity/README.md) for scripting.

## References

- [Hannon Hill: Templates, Configuration Sets, and Outputs](https://www.hannonhill.com/cascadecms/latest/articles/design-in-cascade/templates-formats-outputs.html)
- [Hannon Hill: Formats](https://www.hannonhill.com/cascadecms/latest/articles/developing-in-cascade/script-formats/index.html)
- [Hannon Hill: Velocity Tools](https://www.hannonhill.com/cascadecms/latest/articles/developing-in-cascade/script-formats/velocity-tools.html)
