# SonarQube Server OSS Analysis Workflows

This repository contains preconfigured GitHub Actions workflows that enable automated analysis of open source projects against a SonarQube Server instance. The main purpose is to allow SonarQube Server administrators to test their instance performance and functionality without requiring involvement from project or development teams.

## Purpose

- **Performance Testing**: Run analyses on projects of various sizes to test SonarQube Server performance
- **Instance Validation**: Verify SonarQube Server configuration and functionality
- **Self-Service Testing**: Enable SQS admin or platform teams to trigger sample analyses independently

## How to Use

### Required Configuration

After setting up the repository (see options below), you must configure two repository secrets in your GitHub repository/organization:

- `SONAR_HOST_URL` - The URL of your SonarQube Server instance
- `SONAR_TOKEN` - SonarQube Server user token with the following permissions:
  - Execute analysis
  - Create projects

### Setup Options

#### Option 1: Fork this Repository
1. Fork this repository to your GitHub account/organization
2. **Important**: After forking, you must explicitly enable GitHub Actions in the repository settings
3. Configure the required repository secrets (see above)
4. Trigger workflows manually via GitHub Actions UI (or let them run on push/PR events)

#### Option 2: Download and Re-upload
1. Download this repository as a ZIP file
2. Create a new repository in your GitHub account/organization
3. Upload the contents to your new repository or make the downloaded files a new Git repository and push it to GitHub
4. Configure the required repository secrets (see above)
5. Trigger workflows manually via GitHub Actions UI (or let them run on push/PR events)

## Workflow Structure

The repository includes:
- **Reusable Workflow** (`sonar-scan-cli-oss-prj-reusable.yaml`): Core workflow that performs SonarQube analysis on any specified GitHub repository
- **Caller Workflow** (`call-reusable.yaml`): Example workflow that demonstrates how to use the reusable workflow

## Requirements

- GitHub repository with access to GitHub-hosted runners
- Network connectivity between GitHub runners and your SonarQube Server instance
- Valid SonarQube Server instance with appropriate user permissions configured, valid license
