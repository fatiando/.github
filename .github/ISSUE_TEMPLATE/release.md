---
name: Release Checklist
about: "Maintainers only: Checklist for making a new release"

---

|                   |          Info          |
|:------------------|:-----------------------|
|**Version number** | vX.Y.Z                 |
|**Target date**    | YYYY/MM/DD             | 
|**Zenodo DOI**     | 10.5281/zenodo.4617252 |

## Draft a Zenodo archive (to be done by a manager on Zenodo)

- [ ] Go to the Zenodo entry for this project (find the link to the latest Zenodo release on the `README.md` file)
- [ ] Create a "New version" of it. 
- [ ] Delete all existing files
- [ ] Copy the reserved DOI to this issue
- [ ] Update release date
- [ ] Add as authors any new contributors who have added themselves to `AUTHORS.md`
- [ ] Review author order to make sure it follows the guidelines on our Authorship Guide
- [ ] Save the release draft

## Update the changelog

- [ ] Generate a list of commits between the last release tag and now: `git log HEAD...v1.2.3 > changes.rst`
- [ ] Edit the list to remove any trivial changes (updates by the bot, CI updates, etc).
- [ ] Organize the list into categories (breaking changes, deprecations, bug fixes, new features, maintenance, documentation).
- [ ] 

## Publish to Zeno).

- [ ] Upload the zip archive from the GitHub release to Zenodo
- [ ] Double check all information (date, authors, version)
- [ ] Publish the release
