# Kubernetes Nginx Website Hosting

This project demonstrates hosting a simple Nginx website using Kubernetes. The setup includes a Deployment and a Service to manage and expose the Nginx web server.

## Project Overview

- **Technology Used**: Kubernetes
- **Web Server**: Nginx
- **Components**:
    - **Deployment**: Manages the Nginx pods.
    - **Service**: Exposes the Nginx pods to external traffic.

## Prerequisites

- A Kubernetes cluster set up and running.
- `kubectl` CLI installed and configured to interact with your cluster.
- Git installed to clone the repository.

## Getting Started

1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd <repository-folder>
   ```

2. **Apply the Configuration**:
   - Use the following command to deploy the Nginx website:
     ```bash
     kubectl apply -f deployment.yaml
     kubectl apply -f service.yaml
     ```

3. **Verify the Deployment**:
   - Check the status of the pods:
     ```bash
     kubectl get pods
     ```
   - Check the status of the service:
     ```bash
     kubectl get svc
     ```

4. **Access the Website**:
   - Use the external IP or NodePort provided by the Service to access the Nginx website in your browser.

## Example YAML Files

### Deployment YAML
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
```

### Service YAML
```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  type: NodePort
  selector:
    app: nginx
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
    nodePort: 30007
```

## Notes

- Replace `<repository-url>` with the actual URL of this repository.
- Ensure your Kubernetes cluster allows external traffic to the specified NodePort.

Feel free to contribute or raise issues if you encounter any problems!