# Changelog

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
