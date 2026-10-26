# Developing and Publishing Without a Staging Site

## Purpose

A development or staging site is ideal for testing changes before release. However, some Cascade CMS implementations have **one CMS environment and one live publishing destination**. This guide outlines a conservative workflow for creating or modifying content in that situation.

**Key distinction:** A *hidden or unlinked page on a production website is still public if someone has its URL*. It is **not** a secure staging environment, and it is not isolated from shared CSS, JavaScript, templates, formats, blocks, or scheduled publishing.

**Core safeguard:** Cascade CMS provides an asset-level **Include when publishing** checkbox. Turn this **off on a new development page** to keep that page out of publishing jobs, including a full-site publish. This is a useful, deliberate development practice—not a substitute for staging. Also inspect related files, parent folders, shared assets, and scheduled jobs so you understand the complete release path.

## 1. Inventory before editing

Before accepting a change:

- Identify the affected site, pages, folders, Content Types, Configuration Sets, Templates, Formats, Blocks, Data Definitions, and shared files.
- Identify **every page that uses the affected shared assets**. Cascade's Relationships view can help with this.
- Check whether CSS/JS is served from Cascade-published files, an external repository/CDN, or another host.
- Review available Destinations, Transports, Outputs, scheduled jobs, and Publish Sets.
- Determine whether the site has content approval workflows and who can approve and publish.
- Establish how to restore earlier asset versions **and** how to republish the previous working output.
- Agree on a release window and who will check the published website.

**Stop if a shared change's blast radius or rollback path is unknown.**

## 2. Classify the change

| Change | Main risk | Preferred verification |
| --- | --- | --- |
| Page-only text or content | Limited to one page unless content is reused | Preview, accessibility and link checks |
| New standalone page | Publishing and unintended discovery | Draft/preview; tightly controlled publish if approved |
| Page-specific component | Can still depend on shared assets | Preview and test representative layouts |
| Shared Block or Velocity Format | May affect numerous pages | Relationships review and representative page tests |
| Shared CSS/JavaScript | May affect the whole site immediately when published | Isolated/local test where possible, impact inventory, release plan |
| Template, Configuration Set, or Content Type | Potential site-wide rendering changes | Administrator review; strongly prefer a separate test destination/environment |

## 3. Design and approval before implementation

1. Capture requirements and acceptance criteria, including desktop/mobile behavior and accessibility.
2. Make a mockup or prototype when visual changes need approval.
3. Have the client approve the intended design **before** implementing it in Cascade.
4. Record the agreed scope, affected assets, reviewer, publisher, and rollback owner.

**Example acceptance criteria:** Navigation links are divided into two logical groups; both groups remain keyboard-accessible; mobile navigation and login access remain available; no existing links disappear.

## 4. Develop with the smallest possible scope

**Preferred:** Develop and test the new HTML/CSS/JavaScript independently in a local sandbox or source-controlled project, using representative sample markup. Where feasible, create separate new assets rather than editing live shared ones.

For Cascade-specific changes:

- Use Cascade's draft and preview capabilities before submission when available.
- Use fictional or non-sensitive test content.
- Avoid changing existing shared Templates, Blocks, Formats, CSS, or JavaScript until the impact is assessed.
- Keep a change log listing each modified asset and its previous version.
- Disable **Include when publishing** on each new work-in-progress page, and confirm it remains disabled until release.
- Do not rely on an unlinked folder to protect confidential content.

### Prevent a work-in-progress page from publishing

**Yes: page-level publishing can be disabled.** For a new page that isn't ready for release:

1. Edit the Page in Cascade CMS.
2. Open its **Configure** tab.
3. Uncheck **Include when publishing** and submit the change.
4. Continue editing and previewing the page while keeping it excluded from publishing.
5. Confirm the setting is still disabled before scheduled or full-site publishing occurs.
6. After approval, enable **Include when publishing**, submit, and intentionally publish the approved page to the intended Destination/Output.
7. Verify the live result.

**Why this matters:** Hannon Hill explicitly documents **Include when publishing** for an asset, including protecting a work-in-progress page from publishing jobs. This is a sensible default for draft pages in a site without staging.

**Important nuance:** Disabling this setting does **not** remove previously published content from the web server. If the page was already public, evaluate whether to **Unpublish** it *before* disabling publishing. Disabling the setting can leave the existing public version in place. Likewise, the separate **Include when indexing** checkbox affects Cascade indexing, not publishing.

This page-level safeguard does **not** isolate edits to shared Templates, Formats, Blocks, CSS, or JavaScript. Changes to those assets can affect published pages when relevant content or files are published. It also does not establish that the page is ready for release: approval, tests, publish scope, and rollback still matter.

See [Hannon Hill — Unpublishing vs. Deleting Content](https://www.hannonhill.com/cascadecms/latest/articles/cascade-basics/unpublishing-vs-deleting.html).

## 5. Choose the testing approach

### Option A — CMS draft/preview only (safest for sensitive content)

Use Cascade preview to review layout and content without publishing the draft to the live website. This is useful for content-only changes, but may **not** fully prove production CSS, JavaScript, external assets, integrations, or publish output behavior.

### Option B — Local frontend prototype

Replicate relevant page HTML and styles in a local development project; test breakpoints, keyboard behavior, and scripts there. Validate final Cascade-generated markup separately before release.

### Option C — Temporary published page on the live server (conditional)

Some teams publish sample pages in an unlinked directory. This is **public production testing, not staging**. Use it only with approval and non-sensitive content, and only after verifying:

- The destination and output are the intended ones.
- Automated indexing, navigation, feeds, sitemap generation, and other discovery mechanisms will not expose it unexpectedly; **robots.txt or noindex is not access control**.
- Existing shared assets will not be changed just to make the test page work.
- Any authentication/access restriction, if necessary, is enforced by the **web server or another real access control**, not by a hard-to-guess URL.
- There is a documented removal/unpublish and post-test cleanup plan.

### Option D — Dedicated staging destination or environment

If resources allow, ask the administrator whether a separate Destination pointing to a restricted test server can be provided. This is preferable for shared templating, CSS, JS, and broad changes. A second publishing Destination is not automatically equivalent to an independent Cascade CMS instance; shared CMS assets can still be shared.

## 6. Test and collect approval

For each affected page or component:

- Preview at common desktop, tablet, and mobile widths.
- Test keyboard navigation, visible focus, labels, landmarks, and screen reader-relevant semantics.
- Test links, interactions, loading states, and the absence of browser console errors.
- Review representative pages that share the modified assets.
- Check images, SVG dimensions, and assets with responsive behaviors.
- Verify the intended rendering with the actual output configuration where possible.
- Document known limitations of any preview-only testing.

Send the client an approved preview/mockup or authorized test URL along with a short acceptance checklist. Record explicit approval to release.

## 7. Release safely

1. Confirm the approved scope, affected assets, release window, and rollback owner. For pages held out of publishing, re-enable **Include when publishing** only when approval has been recorded.
2. Save or identify prior working versions of each changed asset.
3. Check the active publishing Destination(s), Output(s), schedules, and publish scope.
4. Publish the **smallest appropriate set of assets** in the agreed order. For shared formats or blocks, confirm which dependent pages need republishing.
5. Review publish notifications and errors.
6. Immediately verify representative live pages, including desktop/mobile and keyboard interactions.
7. Tell the client what changed, what was tested, and any remaining follow-up.

**Avoid publishing the whole site as a default** for a small change.

## Practices worth retaining from a mature development workflow

Even when a client has no DEV instance, preserve the discipline used in a separate-environment release process:

1. **Coordinate shared work:** Avoid simultaneous edits to the same shared Template or Format; assign an owner and a review window.
2. **Keep a version-controlled source of truth where feasible:** Begin from the latest approved code, work on a feature branch, and review differences before deployment.
3. **Build representative test content:** Create a sample page with realistic text, images, links, and edge cases—not merely an empty module.
4. **Review before release:** Provide the reviewer with a preview or safe test artifact plus a summary of the changed assets and expected behavior.
5. **Control the publication boundary:** In environments with separate destinations, temporarily disabling an affected Destination may be part of an administrator-approved release plan. **In single-production-destination environments, do not disable a shared production Destination casually**—use asset-level publish exclusion for unfinished pages and a coordinated release window for shared changes.
6. **Verify in the actual production context:** Even if the component passed a separate test, check the final version on representative live pages.
7. **Communicate the release:** Share the affected pages, a concise description, test results, and any known follow-up.

These are transferable **process principles**. The exact repository branches, review tools, site names, approval channels, and CMS paths must be designed independently for each client. They should not be copied from another organization's internal runbook.

## 8. Rollback and cleanup

If a release fails:

1. Stop further publishes and notify the responsible client contact.
2. Restore the previous working version(s) of relevant Cascade assets or external source files.
3. Republish the affected output and dependent pages as needed. Restoring a CMS version alone does not necessarily revert an already published website.
4. Recheck the live pages, including any cached CSS and JavaScript.
5. Record the cause and revise the procedure.

Remove/unpublish temporary test pages and verify that no unneeded test assets remain publicly available.

## First-access questions for the site owner

- Are there separate CMS environments, separate publishing Destinations, or only one production Destination?
- Who can modify publishing settings and who can publish? Are workflows enabled?
- Are there scheduled full-site, folder, or Publish Set jobs?
- Do test pages sit on the public website? Are they protected, excluded from sitemaps, or simply unlinked?
- Which Templates, Blocks, Formats, CSS, and JS are shared across pages and sites?
- Are there local source files, version control, or a reliable export and rollback process?
- What approval record is required before changes go live?
- Could the administrator provide a restricted staging Destination for higher-risk changes?

## References

- [Hannon Hill — Publishing](https://www.hannonhill.com/cascadecms/latest/articles/content-authoring/publishing/index.html)
- [Hannon Hill — Unpublishing vs. Deleting Content](https://www.hannonhill.com/cascadecms/latest/articles/cascade-basics/unpublishing-vs-deleting.html)
- [Hannon Hill — Creating Content and Preview Draft](https://www.hannonhill.com/cascadecms/latest/articles/cascade-basics/creating-content.html)
- [Hannon Hill — Destinations](https://www.hannonhill.com/cascadecms/latest/content-authoring/publishing/destinations.html)
- [Hannon Hill — Content Types and Publish Options](https://www.hannonhill.com/cascadecms/latest/design-in-cascade/content-types/index.html)
