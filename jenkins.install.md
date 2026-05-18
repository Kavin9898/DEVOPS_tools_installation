## Step 1️⃣ Connect to EC2
ssh -i your-key.pem ec2-user@<EC2-Public-IP>

## Step 2️⃣ Update Server
sudo yum update -y

## Step 3️⃣ Install Java 21 (Required)
```sh
⚠️ New Jenkins versions require Java 21.

Install:

sudo yum install java-21-amazon-corretto -y

Verify:
```sh
java -version
```
Expected:openjdk version "21"
## Step 4️⃣ Add Jenkins Repository
```sh
sudo wget -O /etc/yum.repos.d/jenkins.repo \
https://pkg.jenkins.io/redhat-stable/jenkins.repo
```
Import key:
```sh
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
```
## Step 5️⃣ Install Jenkins
```sh
sudo yum install jenkins -y
```
Verify:
```sh
rpm -qa | grep jenkins
```
## Step 6️⃣ Configure Jenkins to Use Java 21
```
This is the fix for your error.
```sh
sudo systemctl edit jenkins
```
Paste exactly:
```sh
[Service]
Environment="JAVA_HOME=/usr/lib/jvm/java-21-amazon-corretto.x86_64"
```
## Step 7️⃣ Reload Systemd
```sh
sudo systemctl daemon-reload
```
## Step 8️⃣ Start Jenkins
```sh
sudo systemctl start jenkins
sudo systemctl enable jenkins
```
## Step 9️⃣ Verify Jenkins Running
```sh
sudo systemctl status jenkins
```
Expected:

active (running)
## Step 🔟 Open Port 8080 in AWS

In EC2 Security Group:

Add inbound rule:

Type: Custom TCP
Port: 8080
Source: 0.0.0.0/0
## Step 1️⃣1️⃣ Get Admin Password
```sh
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
