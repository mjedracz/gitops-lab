
# CVP - K8s, ArgoCd Lab 

## Deployment
The deployment YAML file deployment.yaml contains the configuration for deploying the application.
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp
spec:
  selector:
    matchLabels:
      app: myapp
  replicas: 4
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
      - name: myapp
        image: nginx:latest
        ports:
        - containerPort: 8080
```
In this deployment configuration, we define a deployment named myapp with 4 replicas. The selector specifies that the deployment should manage pods with the label app: myapp. The template section defines the pod template used for creating the replicas. It contains a single container named myapp running the nginx:latest image, exposing port 8080.

## Service
The service YAML file service.yaml defines the Kubernetes service that exposes the application.
```
apiVersion: v1
kind: Service
metadata:
  name: myapp-service
spec:
  selector:
    app: myapp
  ports:
  - port: 8080
    protocol: TCP
    targetPort: 8080

```
In this service configuration, we define a service named myapp-service that selects pods with the label app: myapp. It exposes port 8080 and forwards incoming traffic to the pods' port 8080 using the TCP protocol.

By combining the deployment and service configurations, you can deploy and expose your application in a Kubernetes cluster.
