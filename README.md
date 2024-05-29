# Solidity Workflows

This repository contains reusable **GitHub Actions workflows** for **Solidity projects**. Each workflow automates specific tasks to ensure code quality, performance, and maintainability.

## Workflows

### 0. Build

This workflow sets up the environment and orchestrates other workflows for building and testing Solidity contracts.

**Steps:**
- Setup: Initializes the environment by checking out code, setting up Node.js, caching node modules, and installing dependencies.
- Test: Runs gas tests to check for gas usage.
- Slither Test: Runs static analysis using Slither.
- Coverage Test: Generates and uploads code coverage reports.

## Usage

To use these workflows in your repository, you can call them from your GitHub Actions workflow files. For example:

```yaml
name: Example Workflow

on:
  push:
    branches:
      - main

jobs:
  build-and-test:
    uses: The-Poolz/solidity-workflows/.github/workflows/build.yml@master
```

### 1. Build and Test Solidity Contracts | The-Poolz

This workflow is designed to set up the environment, run tests, perform static analysis, and generate coverage reports for Solidity contracts. It consists of the following sub-workflows:

- **Setup**: Checks out the code, sets up Node.js, caches node modules, and installs dependencies.
- **Gas Test**: Runs tests to check gas usage and comments on the pull request with a gas report if applicable.
- **Slither Test**: Performs static analysis using Slither and comments on the pull request with a checklist report.
- **Coverage Test**: Runs tests to generate coverage reports and uploads them to Codecov.

### 2. Coverage Test

Runs on demand to generate and upload code coverage reports for Solidity projects.

**Steps:**
- Checkout code.
- Setup Node.js environment.
- Restore node modules cache.
- Run tests and generate coverage using `hardhat coverage`.
- Upload coverage reports to Codecov.

### 3. Gas Test

Runs on demand to test and report gas usage in Solidity contracts.

**Steps:**
- Checkout code.
- Setup Node.js environment.
- Restore node modules cache.
- Run tests with Hardhat and check for gas usage.
- If a gas report is generated, comment on the pull request with the report.

### 4. Publish on Release

Automatically publishes the package to npm when a new release is tagged.

**Steps:**
- Checkout code from the `master` branch.
- Setup Node.js environment.
- Get the release tag from the GitHub ref.
- Configure git user for commits.
- Set the version based on the release tag and push changes.
- Publish the package to npm.

### 5. Setup

Sets up the environment for other workflows by checking out code, setting up Node.js, caching node modules, and installing dependencies.

**Steps:**
- Checkout code.
- Setup Node.js environment.
- Cache node modules.
- Install dependencies if the cache is not hit.

### 6. Slither Test

Runs static analysis using Slither on Solidity contracts to identify potential issues and vulnerabilities.

**Steps:**
- Checkout code from the caller repository.
- Checkout the `solidity-workflows` repository.
- Setup Node.js environment.
- Restore node modules cache.
- Install dependencies if the cache is not hit.
- Run Slither with specified arguments.
- Create or update a checklist as a pull request comment with the Slither report.


## License
This project is licensed under the [MIT License](https://github.com/The-Poolz/solidity-workflows/blob/master/LICENSE).
