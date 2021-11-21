**All of the phases list below are completed and maintained in frontend and backend repo's**
  Frontend Repo: `https://github.com/msannan/DevOps-Project-Backend`
  Backend Repo: `https://github.com/msannan/DevOps-Project-Frontend`

# Project Phase 1 - Docker Compose

You can create any number of microservices you want (2 at least), Better is one of them should connect to database. If you are uncomfortable with coding, You can use the code that was presented in the class(Frontend & Backend)
The microservices each should have their own Github repository.

## Phase 1

If can't use Database in code, so just add a Database service in docker-compose like Mysql or Mongodb with related environment variables.

So you will have at least 2 repositories based on the number of your microservices:

1. **Backend**: Exposes an API endpoint. This repo will contain the backend code, Dockerfile to build image, Docker Compose file to deploy backend and the database.
   `https://github.com/msannan/DevOps-Project-Backend/blob/main/docker-compose.yaml`
2. **Frontend**: Calls the backend and displays the result. This repo will contain the frontend code, Dockerfile to build image, Docker Compose file to deploy frontend, backend, database or any other microservice if added. This will deploy the complete application.
   `https://github.com/msannan/DevOps-Project-Frontend/blob/main/docker-compose.yaml`
 
# Project Phase 2 - CI/CD
You can create any number of microservices you want (2 at least), Better is one of them should connect to database. If you are uncomfortable with coding, You can use the code that was presented in the class(Frontend & Backend)
The microservices each should have their own Github repository.

- Add CI/CD to the microservices repos
- Better to add both Github Actions Workflow and Jenkins but one of them is compulsory
- Whenever some changes are pushed, the pipeline runs, it builds the docker image and pushes to Dockerhub
- You can then update your docker-compose file with new image and run it, and see the updated feature.
**Frontend-CI/CD:`https://github.com/msannan/DevOps-Project-Frontend/blob/main/Jenkinsfile` **
**Backend-CI/CD:`https://github.com/msannan/DevOps-Project-Backend/blob/main/Jenkinsfile` **

For a sample golang-app, you can see the Github Actions workflow at
https://github.com/kahootali/golang-sample-app/tree/master/.github/workflows
It will be same for all language apps, only Dockerfile will change

Github Action to build and push Docker Image
https://github.com/marketplace/actions/build-and-push-docker-images

# Project Phase 3 - K8s

You can create any number of microservices you want (2 at least), Better is one of them should connect to database. If you are uncomfortable with coding, You can use the code that was presented in the class(Frontend & Backend)
The microservices each should have their own Github repository.

## Phase 3

Add Kubernetes  manifests to deploy your application in the repositories
When the pipeline of any of your microservice runs, it will build & push a new docker image tag, so you will update that docker image tag in your K8s manifests and apply it on a Kubernetes cluster i.e. minikube in your case.

The Kubernetes manifest should include
- Deployment file with custom labels, annotations
- Service: exposing frontend on NodePort and backend on Cluster IP
**Frontend-CI/CD:`https://github.com/msannan/DevOps-Project-Frontend/tree/main/K8s` **
**Backend-CI/CD:`https://github.com/msannan/DevOps-Project-Backend/tree/main/K8s` **

# Project Phase 4 - K8s
You can create any number of microservices you want (2 at least), Better is one of them should connect to database. If you are uncomfortable with coding, You can use the code that was presented in the class(Frontend & Backend)
The microservices each should have their own Github repository.

This is optional phase but do try to complete this, as having knowledge is one thing, but once you implement all this, you can easily work on Kubernetes in futureâ€¦

- In Backend Kubernetes Deployment, add Resources for request and limits on memory & CPU (need to read it yourself), add Probes(readiness & liveness).

- Backend should have environment variables NAME and PASSWORD that should be set from a Secret named backend and a file details.txt on path /user/details.txt  that should be set from Configmap named backend where you can have intro about yourself..

- Also in the backend repository add Configmap & Secret manifest files containing above environment variables and file respectively 

- Also add RBAC files to run above deployment with a Service Account with permissions to get, list, watch Pods cluster wide 
- Also if you used DB for your app, try to deploy the DB from the public helm chart
- Can also add helm chart for the application (  Optional ) 

**Link to Phase4**
- Resources+Probes+RBAC+ConfigMap+Secrects: `https://github.com/msannan/DevOps-Project-Frontend/blob/main/K8s/backend.yaml`
- Helm: `https://github.com/msannan/DevOps-Project-Frontend/tree/main/helm`
