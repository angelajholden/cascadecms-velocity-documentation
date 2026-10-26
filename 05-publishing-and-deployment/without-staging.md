# Cascade CMS — Publishing Without a Staging Site

> **Draft — workflow to be confirmed after reviewing the Cascade installation.**
>
> A site with no separate development environment needs extra care when testing changes. These are reference notes, **not a finalized deployment procedure**.

## Known Options

- **Page-level publishing:** For a new work-in-progress page, open **Configure** and disable **Include when publishing**. The page can be edited and previewed without being included in publishing jobs, including full-site publishes.
- **Preview:** Review a draft in Cascade before enabling publishing.
- **Local development:** Test markup, CSS, and JavaScript outside Cascade when possible.
- **Production test pages:** An unlinked published page is still publicly accessible. Use only for approved, non-sensitive tests.
- **Shared assets:** Editing a shared Template, Format, Block, stylesheet, or script may affect existing pages. A page-level publishing setting does not isolate those changes.

**Note:** Disabling publishing does not remove a page already published on the web server. An existing published page may need to be unpublished separately.

## Questions to Answer Before Defining the Process

- [ ] What publishing Destinations and Outputs are configured?
- [ ] Are there scheduled or full-site publishing jobs?
- [ ] Who has permission to publish and approve changes?
- [ ] Which assets are shared across multiple pages?
- [ ] How are changes previewed and approved today?
- [ ] How can previous versions be restored and republished?
- [ ] Is there an approved location or method for testing unpublished work?

## Next Step

Once the installation has been reviewed, replace these notes with a short, tested development → review → approval → publishing checklist.

## Reference

- [Hannon Hill — Cascade CMS Knowledge Base](https://www.hannonhill.com/cascadecms/latest/articles/index.html)
