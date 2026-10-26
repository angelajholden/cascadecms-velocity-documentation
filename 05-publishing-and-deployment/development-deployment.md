# Cascade CMS — Development & Deployment

## Overview

A general workflow for developing, testing, reviewing, and deploying Cascade CMS changes when separate development and production environments are available.

## 1. Local Development

1. Pull the latest changes from the shared development branch.
2. Create a feature branch for your work.
3. Develop and test your code locally.
4. Merge your changes with the development branch and resolve any conflicts.
5. Push your changes to the shared repository.

**Important:** Coordinate with other developers when working on shared Templates or Formats to avoid conflicting changes.

## 2. Cascade DEV

1. Create or update the necessary Formats, Data Definitions, Shared Fields, and other assets.
2. Add the new or updated component to a test page.
3. Populate the test page with representative content, images, and links.
4. Preview the page and test functionality, accessibility, and responsive behavior.
5. Submit your changes for code review.
6. Share the test page with the reviewer for approval.

## 3. Cascade PROD

1. Identify the sites and pages affected by the changes.
2. Coordinate the release and publishing requirements.
3. Temporarily disable the appropriate publishing Destination when necessary and authorized.
4. Apply the approved changes to production.
5. Create or update a test page in the production environment.
6. Preview and verify the changes.
7. Re-enable publishing and publish the necessary assets when approved.
8. Verify the published pages.

**Important:** Changes to shared Templates, Blocks, and Formats can affect multiple pages. Confirm which assets depend on the changes before publishing.

## 4. Final Checks

- [ ] Changes reviewed and approved
- [ ] Desktop and mobile layouts tested
- [ ] Accessibility checked
- [ ] Shared components verified
- [ ] Production publishing settings restored
- [ ] Published pages verified
- [ ] Team notified of completed changes

## Notes

This is a generalized reference workflow. Branch names, code review tools, approval processes, and publishing controls vary by organization.
