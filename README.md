# DevSecOps Pipeline for Voting App

This repository contains the **DevSecOps pipeline implementation** for the **Voting App**. The pipeline integrates various stages to ensure code quality, security, and continuous integration/continuous deployment (CI/CD) to **Azure Kubernetes Service (AKS)**. The pipeline is built using **Azure DevOps**.

## 🛠 Pipeline Overview

The DevSecOps pipeline automates the process of building, testing, scanning, and deploying applications with the following stages:

1. **Maven Compile**: Compile the code using Maven.
2. **Trivy File System Scan**: Perform a security scan using Trivy.
3. **SonarQube Analysis**: Analyze code quality and vulnerabilities using SonarQube.
4. **OWASP Dependency Check**: Perform dependency analysis using OWASP Dependency-Check.
5. **Maven Build**: Build the final application artifact.
6. **Publish to JFrog Artifactory**: Store the build artifacts in JFrog Artifactory.
7. **Docker Build & Push**: Build and push the Docker image to **Azure Container Registry (ACR)**.
8. **Deploy to AKS**: Deploy the application to **Azure Kubernetes Service (AKS)**.

## 🚀 Pipeline Stages

### 1. **Maven Compile**
   - **Task**: Compile the Maven project and resolve dependencies.
   - **Goal**: `maven clean verify`

### 2. **Trivy File System Scan**
   - **Task**: Perform a security scan of the project files using **Trivy**.
   - **Goal**: Generate a scan report in HTML format.

### 3. **SonarQube Analysis**
   - **Task**: Run **SonarQube** static code analysis.
   - **Tools**: SonarQube, Maven
   - **Goal**: Analyze the codebase for potential issues and vulnerabilities.
   - **Steps**:
     - Prepare SonarQube configuration.
     - Perform SonarQube analysis with Maven.

### 4. **OWASP Dependency Check**
   - **Task**: Run **OWASP Dependency-Check** to analyze project dependencies for known vulnerabilities.
   - **Goal**: Check for vulnerable libraries and components in the codebase.

### 5. **Maven Build**
   - **Task**: Build the final JAR file for the Voting App.
   - **Goal**: `maven package`
   - **Artifact**: `voting-app-<version>.jar`

### 6. **Publish to JFrog Artifactory**
   - **Task**: Upload the generated JAR file to **JFrog Artifactory** for versioning and reuse.
   - **Goal**: Store the artifact for future deployment or distribution.

### 7. **Docker Build & Push**
   - **Task**: Build a Docker image and push it to **Azure Container Registry (ACR)**.
   - **Goal**: Containerize the Voting App for easier deployment.

### 8. **Deploy to AKS**
   - **Task**: Deploy the Docker container to **Azure Kubernetes Service (AKS)**.
   - **Goal**: Enable scalable deployment of the application in the cloud.

## ⚙️ Setup and Configuration

### 1. **Prerequisites**

Before setting up the pipeline, ensure the following tools and services are configured:

- **Azure DevOps**: Ensure you have an Azure DevOps account and set up an Azure DevOps organization.
- **Azure Subscription**: You must have an active Azure subscription and configure Azure service connections in Azure DevOps.
- **Azure Kubernetes Service (AKS)**: Set up an AKS cluster and have access credentials.
- **Azure Container Registry (ACR)**: Set up an ACR for storing Docker images.
- **JFrog Artifactory**: Set up JFrog Artifactory to store and manage build artifacts.
- **Trivy**: Install **Trivy** for security scanning of your File System Scan.
- **SonarQube**: Install and configure **SonarQube** for static code analysis.

### 2. **Clone the Repository**

```bash
git clone https://github.com/yourusername/voting-app-java.git
cd voting-app-java

3. Configure Pipeline Variables
The following variables need to be configured in your Azure DevOps pipeline:

azureServiceConnection: Azure service connection for Azure resources.
repositoryName: The repository name in GitHub (e.g., pavan539/voting-app-java).
javaHome: Java home directory path (e.g., /usr/lib/jvm/java-17-openjdk-amd64).
acrName: The name of your Azure Container Registry.
aksResourceGroup: The resource group of your AKS cluster.
aksCluster: The name of your AKS cluster.
namespace: Kubernetes namespace for deployment.
buildVersion: The version of the build, typically 1.0.0-<BuildID>.
4. Configure Azure DevOps Pipeline
To configure the pipeline in Azure DevOps:

Navigate to Pipelines in Azure DevOps.
Click New Pipeline.
Select GitHub as the repository source and authenticate.
Choose YAML for pipeline definition and copy-paste the contents of the pipeline YAML configuration.
5. Access and View Reports
After running the pipeline, you can view the following reports:

Trivy Security Report: Contains results from the file system scan.
SonarQube Code Quality Report: Contains results from static code analysis.
OWASP Dependency Check Report: Contains vulnerability information from the dependency check.
📝 Notes
The pipeline is designed to ensure secure, quality code before it is deployed to AKS.
It uses industry-standard tools like Maven, SonarQube, Trivy, OWASP Dependency-Check, and Docker.
The pipeline integrates Security and Quality Gates as part of a DevSecOps approach.
📧 Contact
GitHub Repository: Your GitHub Repo
LinkedIn: Your LinkedIn Profile
markdown
Copy code

