---
name: Release checklist
about: Tasks that need to be done before a release
title: Release vX.X.X
labels: ''
assignees: ''

---

Draft a Zenodo release:

- [ ] Delete all existing files
- [ ] Reserve a DOI
- [ ] Update version in the title
- [ ] Update release date
- [ ] Add as authors any new contributors who have added themselves to [`AUTHORS.md`](AUTHORS.md)
- [ ] Review author order to make sure it follows the guidelines on our [Authorship Guide](https://github.com/fatiando/contributing/blob/master/AUTHORSHIP.md)
- [ ] Save the release draft

Update the changelog:

- [ ] Generate a list of commits between the last release tag and now: `git log HEAD...vX.X.X > changes.txt`
- [ ] Edit the changes list to remove any trivial changes (updates to the README, typo fixes, CI configuration, etc).
- [ ] Replace the PR number in the commit titles with a link to the GitHub PR page. In Vim, use: ``%s$#\([0-9]\+\)$`#\1 <https://github.com/fatiando/PROJECT/pull/\1>`__$g ``
- [ ] Copy the remaining changes to `doc/changes.rst` under a new section for the intended release.
- [ ] Add a list of people who contributed to the release (use `git shortlog HEAD...v1.2.0 -sne`).
- [ ] Include the Zenodo DOI badge in the changelog. Remember to replace your DOI inside the badge
   url.
- [ ] Add a link to the new release version documentation in `README.rst`
- [ ] Open a new PR with the updated changelog
