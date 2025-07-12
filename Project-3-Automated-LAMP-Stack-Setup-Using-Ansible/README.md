# Project 4: Automated LAMP Stack Setup Using Ansible

## 🧰 Goal

Automate the installation and configuration of a LAMP stack (Linux, Apache, MySQL, PHP) on an EC2 Ubuntu instance using Ansible.

---

## ✅ Project Structure

Project-4-Automated-LAMP-Stack/
├── hosts.ini # Inventory file for Ansible
├── lamp.yml # Ansible playbook
└── README.md # This documentation

---

## 🚀 Steps to Run

### 1. 🖥️ Launch EC2 Instance

- Use **Ubuntu 20.04 or 22.04** AMI
- Open inbound ports **22 (SSH)**, **80 (HTTP)**, **3306 (MySQL)**

### 2. 📝 Configure Inventory (`hosts.ini`)

```ini
[web]
<EC2-PUBLIC-IP> ansible_user=ubuntu ansible_ssh_private_key_file=./devops-key.pem ansible_python_interpreter=/usr/bin/python3

#Replace <EC2-PUBLIC-IP> with your actual EC2 IP.

```

### 3. ▶️ Run the Playbook

```bash
ansible-playbook -i hosts.ini lamp.yml
```

### 4.🌐 Access Your PHP Info Page

```ini
http://<EC2-PUBLIC-IP>/index.php
```
