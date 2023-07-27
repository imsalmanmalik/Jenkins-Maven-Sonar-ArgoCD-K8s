# Spring Boot based Java web application with CI/CD using Jenkins and ArgoCD
 
This is a simple Sprint Boot based Java application that can be built using Maven. Sprint Boot dependencies are handled using the pom.xml 
at the root directory of the repository.

This is a MVC architecture based application where controller returns a page with title and message attributes to the view.

## Execute the application locally and access it using your browser

Checkout the repo and move to the directory

```
git clone https://github.com/imsalmanmalik/Jenkins-Maven-Sonar-ArgoCD-K8s/
cd sprint-boot-app
```

### Accessing the application

Build the Docker Image

```
docker build -t jenkins-cicd-pipeline:v1 .
```

```
docker run -d -p 8010:8080 -t jenkins-cicd-pipeline:v1
```
This would execute the maven target and build the artifacts in a new directory named `target`.

Access the application on `http://<ip-address>:8010`


