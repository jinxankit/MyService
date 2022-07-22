# MyService

Goals: To create my own service from scratch, will add all my learnings here. 

Language: Go

Tasks: Create a basic http methods for movies information.
Things to DO:
Middleware
Authentication
Logging & Errors
add metrics to the service with prometheus
integrate grafana, argocd, and prometheus
Database
Validation
Tests

-- deployment in a docker container --
docker file to kubernetes cluster

- Steps I performed to create docker container:
```sh
- Build the image
docker build -t jinxankit/my-service:latest .
docker tag jinxankit/my-service:latest jinxankit/my-service:v1.0
docker push jinxankit/my-service:v1.0

- Run 
docker run -p 8080:8080 jinxankit/my-service:v1.0
```

- Let's try to test the health of the service:
```sh
curl -X GET http://localhost:8080/health
```

- Steps to deploy the service to kubernetes:
```sh
minikube start

kubectl apply -f k8s-deployment.yaml
kubectl get svc
kubectl get pods
kubectl describe pod
kubectl port-forward deployment/my-service 8080:8080
OR
kubectl port-forward <pod-name> 8080:8080
```

- Steps to test the service:
```sh
curl -X GET http://localhost:8080/health
```

Port forward is a way to test the service locally, but in production, you would want to expose the pod using services.


