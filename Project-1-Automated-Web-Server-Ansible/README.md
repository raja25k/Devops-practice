# Project 1: Automated Web Server Deployment using Ansible

This project automates the setup of an Nginx web server on an AWS EC2 instance using Ansible and Shell scripts.

## 🚀 Technologies Used

- Ansible
- AWS EC2 (Ubuntu)
- Shell Script
- Nginx

## 🛠️ Files

| File                | Description                                    |
| ------------------- | ---------------------------------------------- |
| `inventory.ini`     | Defines the target host (EC2 instance)         |
| `install_nginx.yml` | Ansible playbook to install Nginx              |
| `deploy.sh`         | Shell script to run the playbook automatically |

## ✅ Steps to Run

1. Update `inventory.ini` with your target EC2 IP
2. Make sure passwordless SSH is set up
3. Run:

```bash
bash deploy.sh
```
