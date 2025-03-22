# Auto Changelog Workflow

This repository uses an automated changelog management system that helps maintain consistent changelog entries and automates version bumping based on semantic versioning.

**Disclaimer:** This workflow is in early stages of development. It is simple, but not very flexible yet. It goes without saying, that any contributions are welcome!

[Skip to Project Setup Instructions ➡](#project-setup-instructions)

## How It Works

The workflow automatically manages changelog entries through pull requests and releases.

### Adding Changelog Entries

When creating a pull request, you must include changelog notes in one of two formats:

1. Using changelog tags:
```markdown
/changelog minor
### Added 
* new feature X

### Updated 
* component Y
/-changelog
```

2. Using details element:
```markdown
<details><summary>Changelog minor</summary>

### Added 
* new feature X

### Updated 
* component Y

</details>
```

The change level must be one of:
- `patch`: Bug fixes and minor changes (default level if not provided)
- `minor`: New features (backwards compatible)
- `major`: Breaking changes

![](./docs/pr-description.png)

### Workflow Steps

1. **PR Validation**
   - Validates the changelog entry format
   - Ensures changelog notes are present
   - Checks for valid change level

![](./docs/pr-checks.png)

2. **Changelog Updates**
   - When PR is merged to main, changelog entries are collected
   - Version is bumped according to semantic versioning rules
   - CHANGELOG.md and package.json are updated automatically
   - New version tag is created and pushed

![](./docs/commit-with-changes.png)

3. **Release Creation**
   - When a new release is published from tag:
     - Release notes are automatically populated from the changelog since the last release
     - Previous changes are consolidated into the release notes
     - Original release description is preserved in one of two ways:
       - If `[changelog]` marker is present in description, changelog entries replace the marker
       - Otherwise, changelog entries are appended after the original description

![](./docs/auto-populated-release.png)

## Best Practices

1. Always include changelog entries in your PRs
2. Use appropriate change levels based on the impact of your changes
3. Write clear, concise changelog entries that describe the changes from a user's perspective
4. One change per line in the changelog entry

## Troubleshooting

If the PR validation fails, check:
- Changelog section exists in PR description
- Change level is specified (`patch`, `minor`, or `major`)
- Changelog notes are not empty

## Project Setup Instructions

1. **Configure GitHub Repository Settings**
   - Go to repository Settings > General
   - Under "Pull Requests", enable "Allow squash merging"
   - Check "Default to pull request title and description"
   
2. **Add Local Workflow Files**
   - Create `.github/workflows` directory
   - Add the following workflow files:
      - Enforce the PR description format to match what we can detect:
      ```yaml
         # .github/workflows/validate-changelog.yml
      name: Validate PR Changelog
      
      on:
      pull_request:
         types: [opened, edited, synchronize, reopened]
      
      jobs:
      validate:
         uses: happy-changelog/happy-changelog-workflow/.github/workflows/validate-changelog.yml@v1.0.1
         permissions:
            pull-requests: read
            contents: read
         with:
            changelog-file: CHANGELOG.md
      ```
      - Update changelog and `package.json` after merge/commit into `main`
      ```yaml
         # .github/workflows/update-changelog.yml
      name: Update Changelog
      
      on:
      push:
         branches:
            - main
      
      jobs:
      update:
         uses: happy-changelog/happy-changelog-workflow/.github/workflows/update-changelog.yml@v1.0.1
         permissions:
            contents: write
         with:
            changelog-file: CHANGELOG.md
            enable-npm-version: true
            target-branch: main
            version-title-template: 'v:{level} - {date}'
      ```
      - After publishing a release, update it's description, to contain changelog since previous release
      ```yaml
         # .github/workflows/edit-release.yml
      name: Edit Release Notes
      
      on:
      release:
         types: [published]
      
      jobs:
      release:
         uses: happy-changelog/happy-changelog-workflow/.github/workflows/edit-release.yml@v1.0.1
         permissions:
            contents: write
         with:
            changelog-file: CHANGELOG.md
      ```

3. **Configure Branch Protection**
   - Go to Settings > Branches
   - Add rule for `main` branch
   - Enable "Require status checks to pass"
   - Add "check-pr-description" to required checks
   - Enable "Require squash merging"

4. **Initialize Files**
   - Create `CHANGELOG.md` in repository root and add last known version inside (optional: for fresh projects the file will be initialized for you)
   - Ensure `package.json` exists with version field (for npm packages)

![](./docs/pr-settings.png)

## Important Merge Process
When merging PRs:
- Always use squash merge
- The squash commit message must include the PR description to preserve changelog entries
- The workflow will automatically extract changelog content from the commit message
