# Step 1: Connect to EC2
```sh
ssh -i your-key.pem ec2-user@your-public-ip
```
# Step 2: Update system
```sh
sudo yum update -y
```
# Step 3: Install Docker
```sh
sudo yum install docker -y
```
# Step 4: Start Docker
```sh
sudo systemctl start docker
sudo systemctl enable docker
```
# Step 5: Install kubectl
```sh
curl -LO https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl
```
# Step 6: Make kubectl executable
```sh
chmod +x kubectl
```
# Step 7: Move kubectl to path
```sh
sudo mv kubectl /usr/local/bin/
```
# Step 8: Verify kubectl
```sh
kubectl version --client
```
# Step 9: Install Minikube
```sh
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```
# Step 10: Install Minikube binary
```sh
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```
# Step 11: Start Kubernetes cluster
```sh
sudo minikube start --driver=none
```
# Step 12: Verify cluster
```sh
kubectl get nodes
```
# Step 13: Check pods
```sh
kubectl get pods -A
```
# Step 14: Deploy app
```sh
kubectl create deployment nginx --image=nginx
```
# Step 15: Expose service
```sh
kubectl expose deployment nginx --type=NodePort --port=80
```

# Step 16: Get service
kubectl get svc
