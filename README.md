﻿# Jenkins Shared Library

This repository contains a collection of Jenkins pipeline scripts used for automating various DevOps tasks. The scripts include Docker image management, security scanning, and deployment management. Each script is designed to be reusable and configurable for different Jenkins pipelines.

## Repository Structure

- **`buildDockerImage.groovy`**: 
  
  - **Description**: Contains the pipeline logic for building Docker images.
  - **Inputs**: imageName

- **`checkdeployEksCluster.groovy`**: 
  
  - **Description**: Checks and deploys updates to an EKS cluster.
  - **Inputs**: Credentials, ClusterName, ClusterRegion

- **`dockerHubLogin.groovy`**: 
 
  - **Description**: Handles Docker Hub login while ensuring credentials are hidden.
  - **Inputs**: Credentials

- **`pushDockerImage.groovy`**: 
  
  - **Description**: Logs into Docker Hub and pushes Docker images.

- **`removeDeploymentStage.groovy`**: 
  
  - **Description**: Manages the removal of deployments from the pipeline.

- **`runFlake8Linting.groovy`**: 
  
  - **Description**: Runs Flake8 linting on Python code, and includes Snyk login and Docker image scanning.

- **`sastBanditCheck.groovy`**: 
  
  - **Description**: Integrates Bandit for security checks and Django unit tests, updates Docker Hub login.

- **`snykLogin.groovy`**: 
  
  - **Description**: Manages Snyk login and includes Docker image scanning.
  - **Inputs**: Credentials

- **`snykTestDockerImage.groovy`**: 
 
  - **Description**: Tests Docker images for vulnerabilities using Snyk.
  - **Inputs**: imageName

- **snykTestIas.groovy**:
  - **Description**: Tests IaS for vulnerabilities using Snyk.


- **`trivyScanning.groovy`**: 
  
  - **Description**: Uses Trivy for scanning Docker images for vulnerabilities.
  - **Inputs**: imageName

- **`unitTestDjango.groovy`**: 
  - **Description**: Contains logic for running unit tests on Django applications.

## Usage

To use these scripts in your Jenkins pipeline:

1. **Configure the Shared Library**:
   - Go to **Manage Jenkins** -> **Configure System** -> **Global Pipeline Libraries**.
   - Add a new library with:
     - **Library Name**: Provide a name (e.g., `my-shared-library`).
     - **Source Code Management**: Select `Git` and enter the repository URL.
     - **Branch**: Specify the branch (e.g., `main`).

2. **Include the Library in Your `Jenkinsfile`**:
   ```groovy
   @Library('my-shared-library') _
   // pipeline
   ```
