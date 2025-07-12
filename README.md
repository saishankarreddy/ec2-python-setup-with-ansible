# Ansible Automation: Install Python on AWS EC2 Instances

This project uses Ansible to install Python on multiple AWS EC2 instances automatically and integrates Jenkins for automation.

## 📦 Tools Used
- Ansible
- AWS EC2
- Jenkins (CI/CD)
- SSH Key Authentication
- Ubuntu via WSL (for Windows)

## 🛠️ Setup Instructions

### 1. Inventory File
Update `inventory.ini` with the IPs of your EC2 instances and private key path.

### 2. Run the Playbook

```bash
ansible-playbook -i inventory.ini install_python.yml
```

## 🚀 Jenkins CI/CD Integration

You can automate this playbook execution via Jenkins using the included pipeline.

### Jenkinsfile Example

```groovy
pipeline {
    agent any

    environment {
        INVENTORY = 'inventory.ini'
        PLAYBOOK = 'install_python.yml'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/your-username/python-install-ansible.git'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                sh "ansible-playbook -i ${INVENTORY} ${PLAYBOOK}"
            }
        }
    }
}
```

## ✅ Notes
- Ensure your Jenkins agent has Ansible installed and access to your private key.
- Works for both Amazon Linux and Ubuntu targets.
