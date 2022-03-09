This repo contains:
- Kubernetes Basics
- Example micro service project using Kubernetes

# Project
Project showcase how microservices can be deployed and scaled using kubernetes.

## Object Definitions
### Pod Definitions
Create pod definition files
- voting app: voting-app-pod.yaml
- redis database: redis-pod.yaml
- worker app: worker-app-pod.yaml
- postgres database: postgres-pod.yaml
- result app: result-app-pod.yaml

### Service Definitions
Create service definition files
#### ClusterIP services
- redis service: redis-service.yaml
- postgres service: postgres-service.yaml
#### NodePort services
- voting app service: voting-app-service.yaml
- result app service: result-app-service.yaml

## Deploying and Testing
### Without using deployments
##### Voting app and voting service
```
kubectl create -f pods/voting-app-pod.yaml
kubectl create -f services/voting-app-service.yaml

# list the pods and services
kubectl get pods,svc

# get url of the voting service
minikube service voting-service --url
```

##### Redis and service
```
kubectl create -f pods/redis-pod.yaml
kubectl create -f services/redis-service.yaml

# list the pods and services
kubectl get pods,svc
```

##### Postgres and service
```
kubectl create -f pods/postgres-pod.yaml
kubectl create -f services/postgres-service.yaml

# list the pods and services
kubectl get pods,svc
```

##### Worker
```
kubectl create -f pods/worker-app-pod.yaml

# list the pods
kubectl get pods
```

##### Result app and result service
```
kubectl create -f pods/result-app-pod.yaml
kubectl create -f services/result-app-service.yaml

# list the pods and services
kubectl get pods,svc

# get url of the result service
minikube service result-service --url
```

### With using deployments
##### Voting app deployment and voting service
```
kubectl create -f deployments/voting-app-deploy.yaml
kubectl create -f services/voting-app-service.yaml

# get url of the voting service
minikube service voting-service --url
```

##### Redis deployment and service
```
kubectl create -f deployments/redis-deploy.yaml
kubectl create -f services/redis-service.yaml
```

##### Postgres deployment and service
```
kubectl create -f deployments/postgres-deploy.yaml
kubectl create -f services/postgres-service.yaml
```

##### Worker deployment
```
kubectl create -f deployments/worker-app-deploy.yaml
```

##### Result app deployment and service
```
kubectl create -f deployments/result-app-deploy.yaml
kubectl create -f services/result-app-service.yaml
```

##### Check deployments, pods and svc
```
kubectl get deployments,pods,svc
```

##### Check the app
```
# get url of the voting service
minikube service voting-service --url

# get url of the result service
minikube service result-service --url
```

##### Scale the app
```
# scale voting app
kubectl scale deployments voting-app-deploy --replicas=3

# check voting app deployment
kubectl get deployments voting-app-deploy

# Go to the voting app page and refresh and each time we can see the page is served by different pod.
```

#### References
- [Kubernetes for the Absolute Beginners - Hands-on](https://www.udemy.com/course/learn-kubernetes/)
- [Kubernetes Tutorials](https://kubernetes.io/docs/tutorials/)  
