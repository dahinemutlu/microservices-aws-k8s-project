# Operationalizing a Co-working Space Service
The Coworking Space Service is a set of APIs that enables users to request one-time tokens and administrators to authorize access to a coworking space. This service follows a microservice pattern and the APIs are split into distinct services that can be deployed and managed independently of one another.
This project aims to build a pipeline to deploy an API in Kubernetes that provides business analysts basic analytics data on user activity in the service.

## Dependencies

#### Local Environment
1. Python Environment - run Python 3.6+ applications and install Python dependencies via `pip`
2. Docker CLI - build and run Docker images locally
3. `kubectl` - run commands against a Kubernetes cluster
4. `helm` - apply Helm Charts to a Kubernetes cluster

#### Remote Resources
1. AWS CodeBuild - build Docker images remotely
2. AWS ECR - host Docker images
3. Kubernetes Environment with AWS EKS - run applications in k8s
4. AWS CloudWatch - monitor activity and logs in EKS
5. GitHub - pull and clone code

## Project Implementation Steps
1. Create an Amazon EKS cluster and a managed node group
2. Set up and configure a Postgres database with a Helm Chart
3. Dockerize the application and setup a Continuous Integration with CodeBuild to build and push the Docker image into AWS ECR
5. Create a service and deployment using Kubernetes configuration files to deploy the application
6. Perform an API load test and monitor the performance on CloudWatch

> Please refer to [Project Implementation Report](<./Project Implementation Report.pdf>) for detailed steps.

## Suggestions
1. According to the load test and CloudWatch metrics as mentioned in the [Implementation Report](<./Project Implementation Report.pdf>), the system works smoothly under such load and does not consume too many resources. Since the APIs are simple and do not require much computing power, lower equipped AWS instances (such as t3.small) may be preferred to reduce the cost.
2. For more flexibilty on the observability, other visualization and resource-monitoring tools (such as Grafana, Prometheus etc.) can be deployed.
3. Horizontal Pod Autoscaler (HPA) can be configured on Kubernetes to scale up and down horizontally to address load and help the application to remain elastic and not fail over from traffic.