# Project 2: CI/CD Pipeline with Jenkins

This project demonstrates how to set up a basic Continuous Integration / Continuous Deployment (CI/CD) pipeline using Jenkins. When code is pushed to GitHub, Jenkins automatically builds and deploys the `index.html` file to a web server.

---

## 🎯 Goal

Automatically deploy a static HTML file using Jenkins whenever changes are pushed to a GitHub repository.

---

## 🛠️ Technologies Used

- Jenkins (Freestyle Project)
- GitHub
- Ubuntu (EC2)
- Web Server (Apache/Nginx)

---

## ✅ Steps to Reproduce

### 🧩 Step 1: Install Jenkins on Ubuntu

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
