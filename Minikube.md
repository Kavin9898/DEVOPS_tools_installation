## Step 1: Install kubectl (if not installed)
```sh
curl -LO https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```
## Step 2: Install Minikube
```sh
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
chmod +x minikube-linux-amd64
sudo mv minikube-linux-amd64 /usr/local/bin/minikube
```
## Step 3: Start Minikube using Docker driver
```sh
minikube start --driver=docker
```
👉 This will:
Create a local Kubernetes cluster
Configure kubectl automatically

## Step 4: Verify cluster
```sh
kubectl get nodes
```
✔ Output should show:
minikube   Ready
## Step 5: Check pods
```sh
kubectl get pods -A
```
