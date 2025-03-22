# Contributing Guidelines

Thank you for considering contributing to this project! This document provides guidelines and instructions for contributing.

## Pull Request Process

1. **Changelog Entry Required**
   All pull requests must include a changelog entry in one of these formats:

   Using changelog tags:

    ```markdown
    /changelog [patch|minor|major]

    ### Added
    * your changes here 

    /-changelog
    ```

    Or using details element:

    ```markdown
    <details><summary>Changelog [patch|minor|major]</summary>

    ### Added
    * your changes here

    </details> 
    ```

2.  **Change Levels** Choose the appropriate change level:
    -   `patch`: Bug fixes and minor changes
    -   `minor`: New features (backwards compatible)
    -   `major`: Breaking changes

3.  **Writing Good Changelog Entries**
    -   Write from the user's perspective - mostly devops who will try to implement the workflow
    -   Be clear and concise
    -   One change per line
    -   Group changes under appropriate headers:
        -   `Added` for new features
        -   `Changed` for changes in existing functionality
        -   `Deprecated` for soon-to-be removed features
        -   `Removed` for now removed features
        -   `Fixed` for any bug fixes
  
4.  **Pull Request Guidelines**
    -   Use a clear and descriptive title
    -   Include relevant issue numbers in the description
    -   Keep changes focused and atomic

5.  **Merge Process**
    -   All PRs must be squash merged
    -   The squash commit message must include your PR description to preserve changelog entries
    -   The workflow will automatically handle version bumping and changelog updates

Development Setup
-----------------

1.  Fork the repository
2.  Create a new branch for your changes
3.  Make your changes
4.  Create a pull request with changelog entry
5.  Wait for review and approval

Questions?
----------

If you have questions about contributing, please open an issue in the repository.