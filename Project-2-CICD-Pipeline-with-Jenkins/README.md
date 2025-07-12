# 🚀 Project 2: CI/CD Pipeline with Jenkins

This project demonstrates how to configure a CI/CD pipeline using **Jenkins** on an Ubuntu EC2 instance. The goal is to **automatically build and deploy** a static web page whenever changes are pushed to a GitHub repository.

---

## 🎯 Goal

Automatically deploy `index.html` from GitHub to a web server (`/var/www/html/`) using Jenkins triggered by each GitHub push.

---

## 🛠️ Technologies Used

- Jenkins (Freestyle Project)
- GitHub
- Ubuntu 22.04 (EC2 Instance)
- Nginx (Web Server)

---

## 📋 Project Steps

### ✅ Step 1: Launch Two EC2 Instances

- One for **Control Node (Jenkins)**
- One for **Target Node (Web Server)**

Ensure:
- Both are in the **same VPC**
- Both have ports **22, 80, 8080** open in Security Groups

---

### ✅ Step 2: Install Jenkins on Ubuntu

```bash
sudo apt update
sudo apt install -y fontconfig openjdk-11-jdk

wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian binary/ > /etc/apt/sources.list.d/jenkins.list'

sudo apt update
sudo apt install -y jenkins
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

### ✅ Step 3: Access Jenkins Web UI

- Open Jenkins in browser: http://<your-ec2-public-ip>:8080
- Get the initial admin password:
  sudo cat /var/lib/jenkins/secrets/initialAdminPassword
- Install Suggested Plugins
- Create Admin User
---

### ✅ Step 4: Install Nginx on Target Node 

```bash
sudo apt update
sudo apt install -y nginx
sudo systemctl start nginx
```
- Check if working: http://<target-ec2-ip>/
---

### ✅ Step 5: Create GitHub Repo
- Repository name: html-deploy
- Add file: index.html
```html
<!DOCTYPE html>
<html>
<head><title>CI/CD Test</title></head>
<body>
  <h1>Hello from Jenkins Deployment!</h1>
</body>
</html>
```
- Push this to GitHub
---

### ✅ Step 6: Create Jenkins Job (Freestyle Project)
- Jenkins → New Item → Freestyle project
- Name: html-deploy-pipeline

**Source Code Management**: 
Git URL: https://github.com/<your-username>/html-deploy.git

**Build Triggers**:
- Select: Poll SCM
- Schedule: * * * * * (every minute)

**Build Step → Execute Shell**:
```bash
echo "Deploying..."
cp index.html /var/www/html/
```
Ensure Jenkins user has write access to /var/www/html/
Or adjust permissions:

```bash
sudo usermod -aG sudo jenkins
sudo chown -R jenkins:jenkins /var/www/html
```
---

### ✅ Step 7: Test the CI/CD Pipeline
- Make any update to index.html and push to GitHub
- Jenkins polls the repo every minute
- If there’s a change, it:
  Pulls the latest code
  Runs the build step
  Deploys to web server
-Open: http://<your-jenkins-ec2-ip>/index.html
              or
  http://<target-node-ip>/index.html

You should see the deployed page!
---
