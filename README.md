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

## Screenshots

1. **ArgoCD-UI.png:** This screenshot showcases the ArgoCD user interface displaying the status of the application deployments. It provides a visual representation of the application's health, sync status, and other relevant details.

2. **ArgoCD-secret.png:** This image shows the Kubernetes secret created for ArgoCD. This secret is used to store sensitive information like passwords, tokens, or keys. Kubernetes uses base64 encoded secrets which will generate you a password for your ArgoCD UI and you can proceed with 'admin' as the username. 

3. **Argocd-scv-edit.png:** This screenshot displays the ArgoCD ServiceAccount edit page. It shows the permissions and roles associated with the ServiceAccount. Nanigate to type where the cursor is located at change it to NodePort for accessing ArgoCD UI from your browser. 

4. **dockerhub.png:** This image shows the DockerHub page where the Docker images for the project are stored. It displays the list of repositories, tags, and other details related to the Docker images.

5. **minikube-service-list.png:** This command lists the services our minikube cluster is running locally. you can use the 'example-argocd-server' URL to access the UI.

6. **sonarqube-dashboard-static-code-analysis.png:** This shows the sonarqube dashboard which completes a static code analysis on the build artifact and generates a report. 
   
