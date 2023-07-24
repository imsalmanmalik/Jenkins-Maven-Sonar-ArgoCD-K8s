# Jenkins Pipeline Setup Guide

This guide provides step-by-step details to set up an end-to-end Jenkins pipeline for a Java application using SonarQube, Argo CD, Helm, and Kubernetes.

## Prerequisites

- Java application code hosted on a Git repository
- Jenkins server
- Kubernetes cluster
- Argo CD

## Steps

1. **Install the necessary Jenkins plugins:**
   - Git plugin
   - Maven Integration plugin(here we are using a docker image which has maven pre-installed so this is optional)
   - Docker Pipeline plugin
   - Sonarqube scanner plugin

2. **Create a new Jenkins pipeline:**
   - In Jenkins, create a new pipeline job and configure it with the Git repository URL for the Java application.
   - Add a Jenkinsfile to the Git repository to define the pipeline stages.

3. **Configure Jenkins pipeline stages:**
   - Stage 1: Use the Git plugin to check out the source code from the Git repository.
   - Stage 2: Use the Maven Integration plugin to build the Java application.
   - Stage 3: Use the SonarQube plugin to analyze the code quality of the Java application.
   - Stage 4: Use the Maven Integration plugin to package the application into a JAR file.
   - Stage 5: Use Argo CD to deploy the application onto a kubernetes cluster(here we are using 2 replica pods).

4. **Configure Jenkins pipeline to integrate with Argo CD:**
   - Add the Argo CD API token to Jenkins credentials.
   - Update the Jenkins pipeline to include the Argo CD deployment stage.

5. **Run the Jenkins pipeline:**
   - Trigger the Jenkins pipeline to start the CI/CD process for the Java application.
   - Monitor the pipeline stages and fix any issues that arise.

