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
