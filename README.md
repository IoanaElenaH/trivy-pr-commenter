# Trivy Security Checks

Workflow performs security scans on Terraform files and all code in the repository using Trivy.

## Workflow Overview

1. **Run Trivy Scan for Terraform files**:
   - It runs on every push to the `master` branch and on pull requests targeting the `master` branch.
   - After the scan, it comments on the pr with the scan summary, including the number of critical and high vulnerabilities detected.

2. **Run Trivy Scan for all code**:
   - This job scans all code in the repository for security vulnerabilities using Trivy.
   - It runs on every push to the `master` branch and on pull requests targeting the `master` branch.
   - After the scan, it uploads an HTML report as an artifact and comments on the pull request with a link to the HTML report.

## How to Use

To use this workflow in your repository, follow these steps:

1. **Add Trivy Configuration Files**:
   - Ensure that your repository contains Terraform files and other code that you want to scan for vulnerabilities.
   - Optionally, customize the Trivy configuration by modifying the workflow file.

2. **Configure GitHub Secrets**:
   - Ensure that the necessary GitHub Secrets are configured in your repository settings:
     - `GITHUB_TOKEN`: Required for authentication when interacting with the GitHub API.
     - (Any other secrets required for Trivy or other configurations.)

3. **Trigger the Workflow**:
   - Push changes to the `master` branch or open a pull request targeting the `master` branch to trigger the workflow.

4. **View Results**:
   - Once the workflow completes, review the comments on the pull request for scan summaries and follow the link to the HTML report for detailed scan results.

## Example Usage

```yaml
# .github/workflows/trivy-security-checks.yml
name: Trivy Security Checks

on:
  push:
    branches:
      - master
  pull_request:
    branches:
      - master

jobs:
  # Define jobs here...
