# Changelog

## v1.6.1 - 2025-07-05
### Fixed
* Examples in readme now have correct indentations

## v1.6.0 - 2025-05-18
### Added
* User can now provide custom changelog browser url via `changelog-browser-url`
* User can now change type of url with `changelog-browser-url-type` provided to changelog browser between `default_branch` (uses default branch), `commit` (uses commit SHA) and `tag` (uses version tag)

### Changed
* By default changelog url will now point to default banch

## v1.5.0 - 2025-04-02
### Fixed
* Fixed missing variables in the update-changelog post version script

### Added
* Added `post-version-script` input to various workflows to allow custom
scripts to run after version updates.

### Removed
* Removed `.gitlab-ci.yml` from `.gitignore` as it is no longer needed.

## v1.4.0 - 2025-03-25
### Added
* User can now add `error-on-template` input for `validate-changelog`
which will return error if PR description contains PR template instead
of actual Changelog and description

## v1.3.0 - 2025-03-24
### Added
* Support for markdown pattern: `Changelog` header as block start, and
horizontal line as optional block end

### Changed
* Patterns now are not case sensitive
* All major code is now aligned with gitlab ci

## v1.2.0 - 2025-03-23
### Changed
* use changelog-tools's `--no-strip-markdown` and npms `--allow-same-version`

### Fixed
* jobs now use direct env assignement for `NOTE`
* Fixed incirrect handling of special characters

### Added
* update-changelog job will now set concurrency so that there are no parallel jobs for changelog on `target-branch` file.

## v1.1.0 - 2025-03-22
### Fixed
* incorrect update to changelog file

### Added
* `version-title-template` input variable to `update-changelog.yml`
* `version-title-template` now supports `{version}` and `{date}`
variables

## v1.0.1
### Fixed
* Sections in examples are now appropriately split with additional newline

## v1.0.0
### Changed
* All workflows are now shared

### Added
* Added local run for the workflows to use them on the repo itself

## v0.5.0
### Added
* Add changelog browser url to the release notes

## v0.4.1
### Fixed
* release notes addition works a bit better

## v0.4.0
### Added
* Ability to have your own Release description before body is added
* Added descriptive names for workflow steps

## v0.3.1
### Changed
* Changelog workflow was now split into separate files depending on when
they run
* --------

## v0.3.0
### Updated
* Readme now contains all missing screenshots of workflow

## v0.2.0
### Added
* Readme and images

## v0.1.29
### Fixed
* Fix incorrect var name for jq

## v0.1.28
### Fixed
* Move notes to env variable to fix multiline stuff and quotes

## v0.1.27
### Fixed
* Another fix for multiline strings in release notes (maybe)

## v0.1.26
### Fixed
* Fix multiline release notes

## v0.1.25
### Changed
* Release notes consolidation now takes place only after release is published

## v0.1.24
### Changed
* Try using credentials helper to authenticate tag push
* add explicit user to push

## v0.1.23
### Changed
* add explicit user to push

## v0.1.22
### Changed
* add more debug echos

## v0.1.21
### Changed
* Added -v flag for debugging on tag push

## v0.1.20
### Fixed
* Apparently fixed PAT usage

## v0.1.19
### Changed
* Try username for pat

## v0.1.18
### Changed
* Changed username for tag creation

## v0.1.17
### Changed
* check what happens if pat doesn't have permissions to push

### Removed
* Remove the manual approval as it is not really useful with the way it pauses

## v0.1.16
### Removed
* Remove the manual approval as it is not really useful with the way it pauses

## v0.1.15
### Fixed
* Add permissions for issues on create-release step

## v0.1.14
### Fixed
* Fixed inputs for manual approval

## v0.1.13
### Added
* Manual approval before release

## v0.1.12
### Removed
* Environment: manual
* tag autocreation (for now) as release is not easily done as manual step

## v0.1.11
### Added
* Fake feature 3

## v0.1.10
### Added
* Fake feature 2

## v0.1.9
### Fixed
* environment now correctly moved to separate line

### Added
* an  called

## v0.1.8
### Changed
* Create initial release from all previous tags

## v0.1.7
### Changed
* Use PAT to access last release
* Changed PAT permissions

## v0.1.6
### Changed
* Changed PAT permissions

## v0.1.5
### Changed
* remove debug echo for remotes

## v0.1.4
### Changed
* Added debug echo of remotes

## v0.1.3
### Fixed
* Separate tag push token to ensure new workflow is started after tag push

## v0.1.2
### Fixed
* create-release works on tag push

## v0.1.1
### Fixed
* missing workflow for tag

## v0.1.0
### Fixed
* The script now correctly uses details element for changelog

### Added
* Initial GH Workflow based on gitlab
