
## Step 1: Connect to EC2 instance
```sh
ssh -i your-key.pem ec2-user@your-public-ip
```
## Step 2: Update system packages
```sh
sudo yum update -y
```
## Step 3: Install Docker
```sh
sudo yum install docker -y
```
## Step 4: Start Docker service
```sh
sudo service docker start
```
## Step 5: Enable Docker on boot
```sh
sudo chkconfig docker on
```
## Step 6: Add user to Docker group (avoid sudo every time)
```sh
sudo usermod -aG docker ec2-user
```
## Step 7: Verify Docker installation
```sh
docker --version
```
## Step 8: Test Docker
```sh
docker run hello-world
