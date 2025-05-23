---
name: Release checklist
about: 'Maintainers only: Checklist for making a new release'
title: 'Release vX.Y.Z'
labels: 'maintenance'
assignees: ''

---

**Zenodo DOI:**

<!-- Optional -->
**Target date:** YYYY/MM/DD

## Draft a Zenodo archive (to be done by a manager on Zenodo)

- [ ] Go to the Zenodo entry for this project (find the link to the latest Zenodo release on the `README.md` file)
- [ ] Create a "New version" of it.
- [ ] Get a new DOI for the new release
- [ ] Copy and paste the reserved DOI to this issue
- [ ] Update release date
- [ ] Update version number in Title (make sure there is a leading `v`, like `v1.5.7`)
- [ ] Update version number (use a leading `v` as well)
- [ ] Add as authors any new contributors who have added themselves to `AUTHORS.md` in the same order
- [ ] Ensure that the first author is "Fatiando a Terra Project" and others are listed alphabetically by last name
- [ ] Save the release draft

## Update the changelog

- [ ] Generate a list of commits between the last release tag and now: `git log HEAD...v1.2.3 > changes.md`
- [ ] Edit the list to remove any trivial changes (updates by the bot, CI updates, etc).
- [ ] Organize the list into categories (breaking changes, deprecations, bug fixes, new features, maintenance, documentation).
- [ ] (Optionally) Sort lists in chronological order (i.e. reverse their order). In Vim this can be done by selecting the lines in Visual mode and running `:!tac`.
- [ ] Add a list of people who contributed to the release:
  ```bash
  export last_release="v1.2.3"
  git shortlog HEAD...$last_release -sne > contributors
  git log HEAD...$last_release | grep "Co-authored-by" | sed 's/Co-authored-by://' | sed 's/^[[:space:]]*/ /' | sort | uniq -c | sort -nr | sed 's/^ //' >> contributors
  sort -rn contributors
  ```
- [ ] Add the release date and Zenodo DOI badge to the top
- [ ] Replace the PR numbers with links: ``sed --in-place "s,#\([0-9]\+\),\[#\1\]\(https://github.com/fatiando/PROJECT/pull/\1\),g" changes.md``
- [ ] Check that you changed the ``PROJECT`` placeholder when running the last command.
- [ ] Make a RST copy of the changelog: `pandoc -s changes.md -o changes.rst --wrap=none`
- [ ] Copy the changes to `doc/changes.rst`
- [ ] Add a link to the new release version documentation in `doc/versions.rst`.
- [ ] Build and serve the docs locally with `make -C doc all serve` to check if the changelog looks well
- [ ] Open a PR to update the changelog
- [ ] Merge the PR

## Make a release

After the changelog PR is merged:

- [ ] Draft a new release on GitHub
- [ ] The tag and release name should be a version number (following Semantic Versioning) with a leading `v` (`v1.5.7`)
- [ ] Fill the release description with a Markdown version of the latest changelog entry (including the DOI badge)
- [ ] Publish the release

## Publish to Zenodo

- [ ] Upload the zip archive from the GitHub release to Zenodo
- [ ] Double check all information (date, authors, version)
- [ ] Publish the new version on Zenodo

## Conda-forge package

A PR should be opened automatically on the project feedstock repository.

- [ ] Add/remove/update any dependencies that have changed in `meta.yaml`
- [ ] If dropping/adding support for Python/numpy versions, make sure the correct version restrictions are applied in `meta.yaml`
- [ ] Merge the PR
