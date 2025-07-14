pipeline {
    agent any

    environment {
        INVENTORY = 'inventory.ini'
        PLAYBOOK = 'install_python.yml'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/saishankarreddy/ec2-python-setup-with-ansible.git'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                sh "ansible-playbook -i ${INVENTORY} ${PLAYBOOK}"
            }
        }
    }
}
