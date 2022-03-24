# Project Specification

This project is dedicated to implement CI/CD (Continues Integration and Continues Delivery) for a simple web application on a Kubernetes cluster.

Pipelines lets you build, test, and deploy with continuous integration (CI) and continuous delivery (CD) using GitLab, Tekton and ArgoCD.
### Battle plan:

1. Containerize a web application using `Docker` and `DockerHub`.
   - Install `Docker` 
   - Create a `Dockerfile`
   - Containerize an application
   - Push the docker image to a docker repository (`DockerHub`)

2. Create a `GitHub` code repository.

3. Create infrastructure.
    1. Create VM cluster using `Vagrant`:
   - Admin server (Ansible master, Jenkins + CI/CD tools and plugins)
   - QA server (Sonarqube + DB, Nexus repo)
   - Application servers:
       - Frontend server (Angular, Nginx)
       - Backend server (Java/Nodejs, Apache tomcat)
       - DB server (MySQL, PostgreSQL/MongoDB)

    2. Setup `Minikube`.

4. Setup and start `Tekton`. Use `Tekton` pipelines to build and test application.
   - Install Tekton Pipelines on a Kubernetes cluster
   - Install Tekton CLI
   - Create `Tasks`
   - Create and run `Pipelines`

5. Create `GitLab` image registry. Create `Personal Access Token`. 

6. Setup and start `ArgoCD`. Use `ArgoCD` pipelines to deploying application
7. QA with `Sonarqube`

![Planning](https://cloudnative101.dev/static/e0f59cda603cd30cfc3a5138da9d879c/96d67/tekton-argocd.png)

